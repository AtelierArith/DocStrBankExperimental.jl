EllEnsemble(X::Matrix{T},k :: Kernel)

点の集合とカーネル関数からフルランクのアンサンブルを構築します。

Xは列ベクトル（ColVecs）または行ベクトル（RowVecs）のベクトルであり、kはカーネルです（パッケージKernelFunctions.jlのドキュメントを参照）。

例：円周上の2次元の点と指数カーネル

```
t = LinRange(-pi,pi,10)'
X = vcat(cos.(t),sin.(t))
using KernelFunctions
L=EllEnsemble(ColVecs(X),ExponentialKernel())
```
