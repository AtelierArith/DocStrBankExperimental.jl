```
nystrom_approx(x :: AbstractVector,ker :: Kernel,ind)
```

カーネル行列（カーネル "ker" を使用）を、"ind" でインデックス付けされた行と列を使用して低ランク近似を計算します。

```@example
using KernelFunctions
x = rand(2, 100)
K = kernelmatrix(SqExponentialKernel(), ColVecs(x))
#Kのランク30の近似を構築
V = nystrom_approx(ColVecs(x), SqExponentialKernel(), 1:30)
norm(K - V * V') #小さいはず
```
