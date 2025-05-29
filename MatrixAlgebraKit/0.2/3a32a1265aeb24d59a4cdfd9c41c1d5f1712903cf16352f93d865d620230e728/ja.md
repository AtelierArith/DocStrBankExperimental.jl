```
left_null(A; [kind::Symbol, trunc, alg_qr, alg_svd]) -> N
left_null!(A, [N]; [kind::Symbol, alg_qr, alg_svd]) -> N
```

行列 `A` のコケルネルの直交基底 `N` を計算します。サイズは `(m, n)` で、すなわち `adjoint(A)` のヌル空間であり、`adjoint(A)*N ≈ 0` かつ `N'*N ≈ I` となるようにします。キーワード引数 `kind` を使用して、`A` を因数分解する際に使用する特定の直交分解を指定できます。一方、`trunc` は `A` の特異値を介してランクを制御するために使用できます。

`trunc` は切り捨て戦略オブジェクトまたはフィールド `atol`、`rtol`、`maxnullity` を持つ NamedTuple であることができます。

これは高レベルのラッパーであり、キーワード引数によって制御される `qr!` または `svd!` のいずれかの分解を使用して直交基底 `N` を計算します。

`kind` が提供されると、その可能な値は次のとおりです。

  * `kind == :qr`: `N` は QR 分解を使用して計算されます。これは `isnothing(trunc)` を必要とし、`left_null!(A, [N], kind=:qr)` は `qr_null!(A, [N], alg)` と同等で、デフォルト値 `alg = select_algorithm(qr_compact!, A; positive=true)` が使用されます。
  * `kind == :svd`: `N` は特異値分解を使用して計算され、`trunc` が指定されていない場合はゼロ特異値に対応する左特異ベクトルを含み、`trunc` によって指定された特異値を含みます。

`kind` が提供されない場合、デフォルト値は `isnothing(trunc)` の場合は `:qr` であり、そうでない場合は `:svd` です。最後に、`alg_qr` および `alg_svd` キーワード引数を使用して明示的なアルゴリズムを提供することで、より細かい制御が得られます。これらは対応する因数分解バックエンドでのみ使用されます。`alg_qr` または `alg_svd` が NamedTuples の場合、デフォルトアルゴリズムが `select_algorithm` で選択され、NamedTuple がそのアルゴリズムへのキーワード引数として渡されます。`alg_qr` のデフォルトは `(; positive=true)` であり、デフォルトで正の QR 分解が使用されます。

!!! note
    バン方法 `left_null!` は出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `N` を出力として使用できない場合があるためです。


他にも [`right_null(!)`](@ref right_null)、[`left_orth(!)`](@ref left_orth)、[`right_orth(!)`](@ref right_orth) を参照してください。
