```
abstract type MatrixIntegrator
```

この型は、特定の構造を持つ（行列値の）関数の積分に使用されます。`contour_beyn`および`contour_block_SS`で使用されます。

数値的な数値積分の方法を指定するには、この型を継承する必要があります。

```
julia> abstract type MyIntegrator <: MatrixIntegrator; end
```

そして、メソッド`integrate_interval`を実装します：

```
julia> import NonlinearEigenproblems.NEPSolver.integrate_interval
julia> function integrate_interval(ST::Type{MyType},::Type{T},f,gv,a,b,N,logger) where {T<:Number}
```

関数`integrate_interval`は、区間`[a,b]`で`N`個の数値点を用いて関数を積分する必要があります。その他のパラメータ：

  * 型`T`（通常は`ComplexF64`）は、ターゲットの数値型を指定します。
  * `logger::Logger`は、何をどのようにログに書き込むかを指定します。
  * `f::Function`は、スカラー入力（区間`[a,b]`内）を受け取り、行列またはベクトルを返します。
  * `gv::Vector{Function}`は、スカラー入力（区間`[a,b]`内）を受け取り、スカラーを返します。

関数`integrate_interval`は、最後の次元が`m=length(gv)`であり、積分を含むテンソル`I`を返す必要があります。より正確には、`I[:,:,1]`、... `I[:,:,m]`は、`[a,b]`上での`f(x)gv[1](x)`、...`f(x)gv[m](x)`の積の近似を含む必要があります。例えば、`I[:,:,j]`は次の近似を含む必要があります。

$$
\int_a^b f(x)g_j(x)\,dx
$$

通常、`f(x)`は`g_1(x),..,g_m(x)`を評価するよりもかなり高コストです。

参照：`contour_beyn`、`contour_block_SS`、`MatrixTrapezoidal`
