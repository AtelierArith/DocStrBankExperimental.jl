一般的な漸近的に高速な行列メソッドを提供します：

  * `Strassen.mul` と `Strassen.mul!` はストラスセン方式を使用
  * `Strassen._solve_tril!`
  * `Strassen.lu!`
  * `Strassen._solve_triu`

すべての4つの関数は、基本ケースを使用すべき時期を示すためのキーワード引数 "cutoff" をサポートしています。

速度向上は、環とエントリサイズに依存します。

# 例

```jldoctest
julia> m = matrix(ZZ, rand(-10:10, 1000, 1000));

julia> n1 = similar(m); n2 = similar(m); n3 = similar(m);

julia> n1 = Strassen.mul!(n1, m, m);

julia> n2 = Strassen.mul!(n2, m, m);

julia> n3 = Strassen.mul!(n3, m, m; cutoff = 100);

julia> n1 == n2 == n3
true
```
