```julia
primitive type LinearSolver <: Enum{Int32} 32
```

解法アルゴリズムで線形ソルバーを指定するために使用される公開型。

# 利用可能なオプション

  * `LU`:   LU分解を用いた直接ソルバー。
  * `CHOLESKY`:   コレスキー分解を用いた直接ソルバー。 ヘッセ行列が対称正定値であると想定されるため、デフォルトオプション。
  * `CG`:   共役勾配法を使用した反復ソルバー。
  * `BICGSTAB`:   双共役勾配安定化法を使用した反復ソルバー。
  * `GMRES`:   一般化最小残差法を使用した反復ソルバー。 非対称系に対して収束が証明されているが、多くのメモリを必要とする。
