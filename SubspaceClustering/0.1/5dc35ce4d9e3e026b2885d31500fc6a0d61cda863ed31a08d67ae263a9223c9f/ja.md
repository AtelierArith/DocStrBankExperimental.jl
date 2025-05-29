```
kss(X::AbstractMatrix{<:Real}, d::AbstractVector{<:Integer};
    maxiters = 100,
    rng = default_rng(),
    Uinit = [randsubspace(rng, size(X, 1), di) for di in d])
```

データ行列 `X` の `D×N` データポイント `N` を、対応する部分空間次元 `d[1],...,d[K]` を持つ `K` クラスターに **K**-**s**ub**s**paces (KSS) アルゴリズムを使用してクラスタリングします。出力は、結果のクラスタ割り当て `c[1],...,c[N]`、部分空間基底行列 `U[1],...,U[K]`、およびアルゴリズム実行に関するメタデータを含む [`KSSResult`](@ref) です。

KSS は、以下の総コストを最小化することによってデータポイントをその部分空間でクラスタリングしようとします。

$$
\sum_{i=1}^N \| X[:, i] - U[c[i]] U[c[i]]' X[:, i] \|_2^2
$$

クラスタ割り当て `c[1],...,c[N]` と部分空間基底行列 `U[1],...,U[K]` に関して。

# キーワード引数

  * `maxiters::Integer = 100`: 最大反復回数
  * `rng::AbstractRNG = default_rng()`: 乱数生成器 (空のクラスターのために部分空間を再初期化する際に使用)
  * `Uinit::AbstractVector{<:AbstractMatrix{<:AbstractFloat}}   = [randsubspace(rng, size(X, 1), di) for di in d]`:   使用する `K` の初期部分空間基底行列のベクトル (各 `Uinit[k]` は `D×d[k]` であるべき)

詳細は [`KSSResult`](@ref) を参照してください。
