```
right_null(A; [kind::Symbol, alg_lq, alg_svd]) -> Nᴴ
right_null!(A, [Nᴴ]; [kind::Symbol, alg_lq, alg_svd]) -> Nᴴ
```

行列 `A` のカーネルまたはヌルスペースの直交基底 `N = adjoint(Nᴴ)` を計算します。サイズは `(m, n)` で、`A*adjoint(Nᴴ) ≈ 0` かつ `Nᴴ*adjoint(Nᴴ) ≈ I` となるようにします。キーワード引数 `kind` を使用して、`A` を因数分解する際に使用する特定の直交分解を指定できます。一方、`trunc` は `A` の特異値を介してランクを制御するために使用できます。

`trunc` は、切り捨て戦略オブジェクトまたはフィールド `atol`、`rtol`、`maxnullity` を持つ NamedTuple であることができます。

これは高レベルのラッパーであり、キーワード引数によって制御される `lq!` または `svd!` のいずれかの分解を使用して直交基底 `Nᴴ` を計算します。

`kind` が提供されると、その可能な値は次のとおりです。

  * `kind == :lq`: `Nᴴ` は（非正の）LQ分解を使用して計算されます。これは `isnothing(trunc)` を必要とし、`right_null!(A, [Nᴴ], kind=:lq)` は `lq_null!(A, [Nᴴ], alg)` と同等で、デフォルト値 `alg = select_algorithm(lq_compact!, A; positive=true)` が使用されます。
  * `kind == :svd`: `N` は特異値分解を使用して計算され、`max(atol, rtol * σ₁)` より小さい特異値に対応する左特異ベクトルを含みます。ここで `σ₁` は `A` の最大特異値です。

`kind` が提供されない場合、デフォルト値は `isnothing(trunc)` の場合は `:lq` であり、それ以外の場合は `:svd` です。最後に、`alg_lq` および `alg_svd` キーワード引数を使用して明示的なアルゴリズムを提供することで、より細かい制御が得られます。これらは対応する因数分解バックエンドによってのみ使用されます。`alg_lq` または `alg_svd` が NamedTuples の場合、デフォルトアルゴリズムが `select_algorithm` で選択され、NamedTuple がそのアルゴリズムへのキーワード引数として渡されます。`alg_lq` のデフォルトは `(; positive=true)` であり、デフォルトで正の LQ 分解が使用されます。

!!! note
    バン方法 `right_null!` はオプションで出力構造を受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `Nᴴ` を出力として使用できない場合があるためです。


他にも [`left_null(!)`](@ref left_null)、[`left_orth(!)`](@ref left_orth)、[`right_orth(!)`](@ref right_orth) を参照してください。
