```
left_orth(A; [kind::Symbol, trunc, alg_qr, alg_polar, alg_svd]) -> V, C
left_orth!(A, [VC]; [kind::Symbol, trunc, alg_qr, alg_polar, alg_svd]) -> V, C
```

行列 `A` の画像のための直交正規基底 `V` と、`A` が `A = V * C` と因数分解されるような行列 `C`（コレストリクション）を計算します。キーワード引数 `kind` は、`A` を因数分解するために使用される特定の直交分解を指定するために使用でき、`trunc` は `A` のランクを特異値を通じて決定する際の精度を制御するために使用できます。

`trunc` は、切り捨て戦略オブジェクトまたはフィールド `atol`、`rtol`、および `maxrank` を持つ NamedTuple であることができます。

これは高レベルのラッパーであり、キーワード引数によって制御される直交基底 `V` を計算するために、[`qr_compact!`](@ref)、[`svd_compact!`](@ref)/[`svd_trunc!`](@ref)、および[`left_polar!`](@ref) のいずれかの分解を使用します。

`kind` が提供されると、その可能な値は次のとおりです。

  * `kind == :qr`: `V` と `C` は QR 分解を使用して計算されます。これは `isnothing(trunc)` を必要とし、`left_orth!(A, [VC])` はデフォルト値 `alg = select_algorithm(qr_compact!, A; positive=true)` を持つ `qr_compact!(A, [VC], alg)` と同等です。
  * `kind == :polar`: `V` と `C` は極分解を使用して計算されます。これは `isnothing(trunc)` を必要とし、`left_orth!(A, [VC])` はデフォルト値 `alg = select_algorithm(left_polar!, A)` を持つ `left_polar!(A, [VC], alg)` と同等です。
  * `kind == :svd`: `V` と `C` は、`trunc` キーワード引数を使用して切り捨て戦略が指定されている場合は特異値分解 `svd_trunc!` を使用して計算され、それ以外の場合は `svd_compact!` を使用して計算されます。`V` には左特異ベクトルが含まれ、`C` は特異値と右特異ベクトルの積として計算されます。すなわち、`U, S, Vᴴ = svd(A)` の場合、`V = U` および `C = S * Vᴴ` となります。

`kind` が提供されない場合、デフォルト値は `isnothing(trunc)` の場合は `:qr`、それ以外の場合は `:svd` です。最後に、`alg_qr`、`alg_polar`、および `alg_svd` キーワード引数を通じてバックエンド因数分解のための明示的なアルゴリズムを提供することで、より細かい制御が得られます。これらは、他の入力に基づいて対応する因数分解が呼び出された場合にのみ使用されます。`alg_qr`、`alg_polar`、または `alg_svd` に NamedTuples が渡されると、デフォルトのアルゴリズムが `select_algorithm` で選択され、その NamedTuple がそのアルゴリズムへのキーワード引数として渡されます。`alg_qr` のデフォルトは `(; positive=true)` であるため、デフォルトでは正の QR 分解が使用されます。

!!! note
    バン方法 `left_orth!` はオプションで出力構造を受け入れ、入力行列 `A` を破壊する可能性があります。関数の戻り値を常に使用してください。提供された `CV` を出力として使用できない場合があるためです。


他にも [`right_orth(!)`](@ref right_orth)、[`left_null(!)`](@ref left_null)、[`right_null(!)`](@ref right_null) を参照してください。
