```julia
fdrand(, nx; ...)
fdrand(, nx, ny; ...)
fdrand(, nx, ny, nz; matrixtype, update, rand, symmetric)
fdrand(nx; ...)

```

単位ハイパーキューブ $\Omega\subset\mathbb R^d$ 上のランダム係数を持つ拡散問題のためのモック有限差分演算子の行列を作成します。`nx>1 && ny==1 && nz==1` の場合は $d=1$、`nx>1 && ny>1 && nz==1` の場合は $d=2$、`nx>1 && ny>1 && nz>1` の場合は $d=3$ です。対称の場合、これは次のように対応します。

$$
    \begin{align*}
             -\nabla a \nabla u &= f&&  \text{in}\;  \Omega  \\
    a\nabla u\cdot \vec n + b u &=g && \text{on}\;  \partial\Omega
    \end{align*}
$$

この行列は、不可約対角優位であり、主対角成分は正、非対角成分は非正であるため、M-Propertyを持ちます。したがって、その逆行列は正の成分を持つ密な行列になります。また、ヤコビ反復行列のスペクトル半径 $ho(I-D(A)^{-1}A)<1$ です。

さらに、対称の場合、これは正定値です。

パラメータ + デフォルト値：

|                   パラメータ + デフォルト値 | 説明            |
| --------------------------------:|:------------- |
|                             `nx` | x方向の未知数の数     |
|                             `ny` | y方向の未知数の数     |
|                             `nz` | z方向の未知数の数     |
|   `matrixtype = SparseMatrixCSC` | 行列の種類         |
| `update = (A,v,i,j)-> A[i,j]+=v` | 要素更新関数        |
|              `rand =()-> rand()` | ランダム数生成器      |
|                 `symmetric=true` | 対称行列を作成するかどうか |

スパース構造は直交グリッドに固定されており、次元に応じて3、5、または7の対角行列になります。エントリはランダムですが、例えば `rand=()->1` をランダム数生成器として渡すと、ランダムではなくなります。Matrix、SparseMatrixCSC、ExtendableSparseMatrix、Tridiagonal、SparseMatrixLNK、`：COO` でテスト済みです。
