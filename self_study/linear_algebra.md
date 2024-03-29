# linear algebra.

## hello.

3Blue1Brown series, [Essence of linear algebra](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab). Online textbook, [Interactive Linear Algebra](https://textbooks.math.gatech.edu/ila/), by Dan Margalit and Joseph Rabinoff.

## vectors?

In **physics**, vectors are *arrows pointing in space*, defined by their direction and their length. This is the interpretation that I learned in my high school calculus, and physics classes.

In **computer science**: vectors are *ordered lists of numbers*. This interpretation is very useful for data analysis when you need to represent groups of different observations/features. The dimension of the vector is the length of the list, a 2D-vector would have two features in it.

More generally, however, **vectors** are any structure such that those structures interact with each other according to a set of axioms. This perspective seeks to generalize both the above interpretations and more. The form that vectors take doesn't matter! As long as they can be added and scaled according to these axioms.

The 8 **axioms** are as follows:
- $\vec{u} + (\vec{v} + \vec{w}) = (\vec{u} + \vec{v}) + \vec{w}$.
- $\vec{v} + \vec{w} = \vec{w} + \vec{v}$.
- There is a vector $\mathbb{0}$ such that $\mathbb{0} + \vec{v} = \vec{v}$ for all $\vec{v}$.
- For all $\vec{v}$, there exists $-\vec{v}$ such that $\vec{v} + (-\vec{v}) = \mathbb{0}$.
- $a(b\vec{v}) = (ab)\vec{v}$.
- $1\vec{v} = \vec{v}$.
- $a(\vec{v} + \vec{w}) = a\vec{v} + a\vec{w}$.
- $(a + b)\vec{v} = a\vec{v} + b\vec{v}$.

No need to memorize these or anything, but they provide a very good and naturally intuitive understanding for what defines a vector: the existence of **vector addition** and **scalar-vector** multiplication!

The term **scalar** refers to any "number." Why this term? Because if we look at what multiplying a number by a vector does visually (think of the physics perspective of a vector), it *scales* the vector by that number!

**Vector addition** is pretty straightforward:
$$
\begin{bmatrix}
a \\
b \\
c
\end{bmatrix}
+
\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}
=
\begin{bmatrix}
a + x \\
b+y \\
c+z
\end{bmatrix}
$$
**Scalar-vector multiplication** effectively *scales* each component of the vector:
$$
c
\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}
=
\begin{bmatrix}
c*x \\
c*y \\
c*z
\end{bmatrix}
$$
**Vector subtraction** is easier to think about when expressed as a combination of addition and scaling:
$$
\begin{bmatrix}
a \\
b \\
c
\end{bmatrix}
-
\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}
=
\begin{bmatrix}
a \\
b \\
c
\end{bmatrix}
+ (
-1
\begin{bmatrix}
x \\
y \\
z
\end{bmatrix}
) =
\begin{bmatrix}
a \\
b \\
c
\end{bmatrix}
+
\begin{bmatrix}
-x \\
-y \\
-z
\end{bmatrix}
=
\begin{bmatrix}
a-x \\
b-y \\
c-z
\end{bmatrix}
$$

## subspaces, basis, and spans.

What we visually consider the $xy$-plane can be mathematically expressed as $\mathbb{R}^2$, the set of all possible pairs of two real numbers. Not all of our work will take place in $\mathbb{R}^2$, sometimes we want to focus on subsets of it. 

A **subspace** $V$ is a specific kind of subset in $\mathbb{R}^n$ where:

- The zero vector is in $V$.
- If $\vec{u}$ and $\vec{v}$ are in $V$, then $\vec{u} + \vec{v}$ is also in $V$.
  - Closure under vector addition.
- If $\vec{v}$ is in $V$ and $a$ is in $R$, then $a\vec{v}$ is also in $V$.
  - Closure under scalar multiplication.

We define our coordinate system in terms of basis vectors. In 2 dimensions, we have two basis vectors, one for each dimension. Every possible vector in this dimension, is internally written as some linear combination of the basis vectors. 

A **linear combination** is essentially some expression that involves vector addition and/or scalar-vector multiplication.

We most often use the following basis vectors, as they make representing other vectors very convenient (a number multiplied by $1$ is just itself): 
$$
\vec{i} = \begin{bmatrix} 1 \\ 0 \end{bmatrix} &
\vec{j} = \begin{bmatrix} 0 \\ 1 \end{bmatrix}
$$
Thanks to the simplicity of our basis vectors, we can easily rewrite any vector (like the one below) as a linear combination of them. 
$$
\begin{align*}
\begin{bmatrix}
2 \\ 
3
\end{bmatrix} 
= 2
\begin{bmatrix}
1 \\
0
\end{bmatrix}
+ 3
\begin{bmatrix}
0 \\
1
\end{bmatrix}
= 2\vec{i} + 3\vec{j}
\end{align*}
$$
Let's flesh out our definition a bit: **basis vectors** are a set of vectors that can be linearly combined to form any possible vector that lies in our coordinate space. See how the expression $a\vec{i} + b\vec{j}$ can result in any possible vector in the 2d space, given the correct values of $a$ and $b$?

Now we introduce a new term, the span. The **span** of vectors $\vec{v}$ and $\vec{w}$ is the set of all of their linear combinations, i.e. the set containing $a\vec{v} + b\vec{w}$ where $a$ and $b$ both vary over all real numbers. 
$$
\operatorname{Span}\set{\vec{v_1}, \vec{v_2}, \dots, \vec{v_m}} = \set{c_1\vec{v_1}, c_2\vec{v_2}, \dots, c_m\vec{v_m} \mid c_1, c_2, \dots, c_m \in \mathbb{R}}
$$
Think about the similarities in our definitions of the **basis vectors** and **span**. 

Let's refine our definition again: a basis of a subspace $V$ is some set of vectors $\set{\vec{v_1}, \vec{v_2}, \dots, \vec{v_m}}$ such that $V = \operatorname{Span}\set{\vec{v_1}, \vec{v_2}, \dots, \vec{v_m}}$. Why does this make sense? Well, in order for some set of vectors to be a basis of a subspace, they must *span* the entire subspace. In other words, the set of their linear combinations must be equivalent to the subspace.

## introducing linear transformations!

A **transformation** is essentially a specific function that takes in a vector, and outputs a vector. Considering a transformation can take in and output an infinite number of vectors in a space, we can visualize a transformation as shifting the coordinate plane itself. This is well explained visually in the [3b1b video](https://www.youtube.com/watch?v=kYB8IZa5AuE&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=3&t=224s).

Transformations can often have chaotic and complex effects on the vectors they take in, which is why linear algebra focuses on a specific type that are easier to understand and represent mathematically: the **linear transformation.**

A **linear transformation** takes the following properties visually:

- Straight lines in the original plane remain straight in the transformed plane.
- The origin must remain fixed in place before and after the transformation.
- "Grid lines remain parallel and evenly spaced."

To represent a linear transformation numerically, we only need to record how the basis vectors, $\vec{i}$ and $\vec{j}$ change when transformed. This is because we can determine how any vector in the span of the basis will be transformed just from knowing what happens to the basis vectors!

Let's say we have some transformation that changes the basis vectors in the following manner:
$$
\vec{i}:
\begin{bmatrix}
1 \\ 
0
\end{bmatrix}
\rightarrow
\begin{bmatrix}
2 \\
3
\end{bmatrix}
&
\vec{j}:
\begin{bmatrix}
0 \\ 
1
\end{bmatrix}
\rightarrow
\begin{bmatrix}
4 \\
5
\end{bmatrix}
$$
How would the vector $\vec{u} = \begin{bmatrix}2 \\ 3\end{bmatrix}$ change under the transformation described above? 

Note that the linear combination of $\vec{u}$ in terms of $\vec{i}$ and $\vec{j}$ stays the same before and after the transformation. In other words, if $\vec{u} = a\vec{i} + b\vec{j}$, then $\vec{u}_{f} = a\vec{i}_{f} + b\vec{j}_{f}$. All we need to find are $a$ and $b$, which are pretty easy to find with our choice of basis vectors. (Also, the $f$ subscript here just refers to the transformed equivalents of those vectors).
$$
\vec{u} = \begin{bmatrix}2 \\ 3\end{bmatrix} = 2\begin{bmatrix}1 \\ 0\end{bmatrix} + 3\begin{bmatrix}0 \\ 1\end{bmatrix} = 2\vec{i} + 3\vec{j}
\\\\

\vec{u}_{f} = 2\vec{i}_{f} + 3\vec{j}_{f} 
= 2\begin{bmatrix}2 \\ 3\end{bmatrix} + 3\begin{bmatrix}4 \\ 5\end{bmatrix} = \begin{bmatrix}16 \\ 21\end{bmatrix}
$$
And there's our answer! From just the resulting transformed vectors of $\vec{i}$ and $\vec{j}$, we can find the output of the transformation of any vector in our space.

## matrices as linear transformations.

In essence, a two-dimensional linear transformation can be described by just four numbers: the $x$ and $y$-coordinates of where $\vec{i}$ lands, and those of where $\vec{j}$ ends up. We often package these numbers into a grid, called a **transformation matrix**. Let's write the matrix $A$ for the transformation we used in the last section.
$$
A = \begin{bmatrix}
2 & 4 \\
3 & 5
\end{bmatrix}
$$
Notice what the numbers correspond to:

- The first column is quite literally where $\vec{i}$ lands after being transformed; the second column is where $\vec{j}$ ends up after being transformed.
- And the first row contains $x$-coordinates; the second row holds $y$-coordinates.

It's pretty easy to expand a transformation matrix into three (or more) dimensions. We just add more columns depending on the basis vectors we have, and more rows for the dimensions of each vector!

Writing transformations as matrices allows us to more concisely represent them with equations. Let's call our example transformation $T(\vec{x})$, noting that it takes in a vector $x$ that gets transformed. We can define $T(\vec{x})$ as follows:
$$
T(\vec{x}) = A\vec{x}
= \begin{bmatrix}
2 & 4 \\
3 & 5
\end{bmatrix}
\vec{x}
$$
What is this saying? Well, to apply the transformation $T$ onto the vector $\vec{x}$, we want to multiply $\vec{x}$ by $A$, thereby applying the transformation matrix onto the vector. 

Say we have a vector $\vec{u}$, with components $u_x$ and $u_y$, and want to apply the transformation on matrix $A$ to it.
$$
T(\vec{u}) = A\vec{u}
= \begin{bmatrix}
2 & 4 \\ 
3 & 5
\end{bmatrix}\vec{u} = 
\begin{bmatrix}
2 & 4 \\ 
3 & 5
\end{bmatrix}
\begin{bmatrix}
u_x \\
u_y
\end{bmatrix} = 
u_x \begin{bmatrix}
2 \\
3
\end{bmatrix} + 
u_y \begin{bmatrix}
4 \\
5
\end{bmatrix} = \dots
$$
Try to understand what's happening here. We're taking each component of our vector $\vec{u}$ and multiplying it by the transformation of its respective basis vector! 

Let's parallel this to how we transformed vector $\vec{u} = \begin{bmatrix}2 \\ 3 \end{bmatrix}$ before, without using a transformation matrix.
$$
T(\vec{u}) =
A\vec{u}
= 
\begin{bmatrix}
2 & 4 \\ 
3 & 5
\end{bmatrix}
\begin{bmatrix}
2 \\
3
\end{bmatrix} = 
2 \begin{bmatrix}
2 \\
3
\end{bmatrix} + 
3 \begin{bmatrix}
4 \\
5
\end{bmatrix} = \begin{bmatrix}16 \\ 21\end{bmatrix}
$$
Look at the step before our answer. Doesn't that match up exactly with what we came to originally, when we directly multiplied $\vec{u}$'s components by the transformations of the basis vectors? Matrices are a convenient package for us to represent transformations, and (contrary to my original belief) **matrix-vector** multiplication is actually a very intuitive process when looked at this way.

## multiple transformations and matrix multiplication.

How can we represent consecutive transformations mathematically? Let's say we want to first rotate a vector by $-90\degree$ about the origin, and then shear it so that $\vec{j}$ lands on $\begin{bmatrix} 2 \\ 5 \end{bmatrix}$.

Let's first try to represent these two transformations as their own matrix. For the $-90\degree$ rotation, how will our basis vectors move?
$$
\vec{i}: \begin{bmatrix}1 \\ 0\end{bmatrix} \rightarrow \begin{bmatrix}0 \\ 1\end{bmatrix} & &
\vec{j}: \begin{bmatrix}0 \\ 1\end{bmatrix} \rightarrow \begin{bmatrix}-1 \\ 0\end{bmatrix}
\\
& T_1(\vec{x}) = \begin{bmatrix}0 & -1 \\ 1 & 0\end{bmatrix}\vec{x}
$$
And for our shear transformation:
$$
\vec{i}: \begin{bmatrix}1 \\ 0\end{bmatrix} \rightarrow \begin{bmatrix}1 \\ 0\end{bmatrix} & &
\vec{j}: \begin{bmatrix}0 \\ 1\end{bmatrix} \rightarrow \begin{bmatrix}2 \\ 5\end{bmatrix}
\\
& T_2(\vec{x}) = \begin{bmatrix}1 & 2 \\ 0 & 5\end{bmatrix}\vec{x}
$$


Take a minute to map out graphically why this makes sense, if you haven't understood it already. Let's say we wanted to apply $T_1$, and then $T_2$. Essentially, taking the output of $T_1$ and then inputting it into $T_2$.
$$
T_2(T_1(\vec{x})) = \begin{bmatrix}1 & 2 \\ 0 & 5\end{bmatrix}\begin{bmatrix}0 & -1 \\ 1 & 0\end{bmatrix}\vec{x}
$$
But can we represent this new, combined transformation with one matrix?

Recall that a transformation matrix holds the locations of the transformed basis vectors. So, to find the transformation matrix of our combined transformation, we need to determine the location of the basis vectors after they undergo $T_1$, and then $T_2$.

We know that $\vec{i}$ will land at $\begin{bmatrix}0 \\ 1\end{bmatrix}$ after $T_1$, so it must land at $T_2(\begin{bmatrix}0 \\ 1\end{bmatrix})$ after both transformations. In the same vein, $\vec{j}$ must end up at $T_2(\begin{bmatrix}-1 \\ 0\end{bmatrix})$ after both transformations. Let's evaluate these expressions.
$$
\vec{i} \rightarrow T_2(T_1(\vec{i})) = 
T_2(\begin{bmatrix}0 \\ 1\end{bmatrix}) = 
\begin{bmatrix}1 & 2 \\ 0 & 5\end{bmatrix}\begin{bmatrix}0 \\ 1\end{bmatrix} = 
0\begin{bmatrix}1 \\ 0\end{bmatrix} + 1\begin{bmatrix}2 \\ 5\end{bmatrix} = 
\begin{bmatrix}2 \\ 5\end{bmatrix}

\\\\

\vec{j} \rightarrow T_2(T_1(\vec{j})) = 
T_2(\begin{bmatrix}-1 \\ 0\end{bmatrix}) =
\begin{bmatrix}1 & 2 \\ 0 & 5\end{bmatrix}\begin{bmatrix}-1 \\ 0\end{bmatrix} =
-1\begin{bmatrix}1 \\ 0\end{bmatrix} + 0\begin{bmatrix}2 \\ 5\end{bmatrix} = 
\begin{bmatrix}-1 \\ 0\end{bmatrix}

\\\\

T_{1\rightarrow2}(\vec{x}) = \begin{bmatrix}2 & -1 \\ 5 & 0\end{bmatrix}\vec{x}
$$
And just like that! We've found a matrix that combines both transformations, in that order, into one! Through the process above, we've performed **matrix multiplication**. Interpreting matrix multiplication as performing multiple linear transformations consecutively makes the concept much more intuitive.

Things to remember:

- *Order matters*. If you apply two rotations, the order won't matter. But there are cases where applying two transformations in different orders will have different outcomes, so keep that in mind.
- Go right-to-left order when multiplying matrices. Just thinking about it like regular multiplication, this might not make sense. But thinking about it in terms of nested transformation functions, i.e. $T_2(T_1(\vec{x}))$, will make this more intuitive.

## determinants!

Put concisely, the **determinant** of a transformation is the factor by which it scales areas in the initial space. An easy way to understand the determinant (of a $\mathbb{R}^2$) visually is to measure the change in area of the $1$x$1$ unit square.

The determinant can be negative, which signifies that the orientation of that $1$x$1$ square has flipped.

