*Classical Multidimensional Scaling* (MDS), also known as Principal Coordinates Analysis (PCoA), is a specific technique in this family that accomplishes the embedding in two steps:

1. Convert the distance matrix to a Gram matrix. This conversion is based on

the following relations between a distance matrix $D$ and a Gram matrix $G$:

$$
\mathrm{sqr}(\mathbf{D}) = \mathbf{g} \mathbf{1}^T + \mathbf{1} \mathbf{g}^T - 2 \mathbf{G}
$$

Here, $\mathrm{sqr}(\mathbf{D})$ indicates the element-wise square of $\mathbf{D}$, and $\mathbf{g}$ is the diagonal elements of $\mathbf{G}$. This relation is itself based on the following decomposition of squared Euclidean distance:

$$
\| \mathbf{x} - \mathbf{y} \|^2 = \| \mathbf{x} \|^2 + \| \mathbf{y} \|^2 - 2 \mathbf{x}^T \mathbf{y}
$$

2. Perform eigenvalue decomposition of the Gram matrix to derive the coordinates.

*Note:*  The Gramian derived from $D$ may have non-positive or degenerate eigenvalues.  The subspace of non-positive eigenvalues is projected out of the MDS solution so that the strain function is minimized in a least-squares sense.  If the smallest remaining eigenvalue that is used for the MDS is degenerate, then the solution is not unique, as any linear combination of degenerate eigenvectors will also yield a MDS solution with the same strain value.
