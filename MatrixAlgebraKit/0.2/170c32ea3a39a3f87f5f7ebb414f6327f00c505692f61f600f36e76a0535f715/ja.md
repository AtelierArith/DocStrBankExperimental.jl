```
right_orth(A; [kind::Symbol, trunc, alg_lq, alg_polar, alg_svd]) -> C, Vᴴ
right_orth!(A, [CVᴴ]; [kind::Symbol, trunc, alg_lq, alg_polar, alg_svd]) -> C, Vᴴ
```

行列 `A` の共像のための直交基底 `V = adjoint(Vᴴ)` を計算します。すなわち、`adjoint(A)` の像のための基底と、`A = C * Vᴴ` を満たす行列 `C` を計算します。キーワード引数 `kind` は、`A` を因数分解するために使用される特定の直交分解を指定するために使用できます。一方、`trunc` は、特異値を介して `A` のランクを決定する際の精度を制御するために使用できます。

`trunc` は、切り捨て戦略オブジェクトまたは `atol`、`rtol`、`maxrank` フィールドを持つ NamedTuple であることができます。

これは高レベルのラッパーであり、キーワード引数によって制御される直交基底 `V` を計算するために、[`lq_compact!`](@ref)、[`svd_compact!`](@ref)/[`svd_trunc!`](@ref)、および [`right_polar!`](@ref) のいずれかの分解を使用します。

`kind` が提供される場合、その可能な値は次のとおりです。

  * `kind == :lq`: `C` と `Vᴴ` は QR 分解を使用して計算されます。これは `isnothing(trunc)` を必要とし、`right_orth!(A, [CVᴴ])` は `lq_compact!(A, [CVᴴ], alg)` と同等で、デフォルト値は `alg = select_algorithm(lq_compact!, A; positive=true)` です。
  * `kind == :polar`: `C` と `Vᴴ` は極分解を使用して計算されます。これは `isnothing(trunc)` を必要とし、`right_orth!(A, [CVᴴ])` は `right_polar!(A, [CVᴴ], alg)` と同等で、デフォルト値は `alg = select_algorithm(right_polar!, A)` です。
  * `kind == :svd`: `C` と `Vᴴ` は、`trunc` キーワード引数を使用して切り捨て戦略が指定されている場合は特異値分解 `svd_trunc!` を使用して計算され、それ以外の場合は `svd_compact!` を使用して計算されます。`V = adjoint(Vᴴ)` には特異値に対応する右特異ベクトルが含まれ、`C` は特異値と右特異ベクトルの積として計算されます。すなわち、`U, S, Vᴴ = svd(A)` の場合、`C = rmul!(U, S)` および `Vᴴ = Vᴴ` となります。

`kind` が提供されない場合、デフォルト値は `isnothing(trunc)` の場合は `:lq`、それ以外の場合は `:svd` です。最後に、`alg_lq`、`alg_polar`、および `alg_svd` キーワード引数を介してバックエンドの因数分解のために明示的なアルゴリズムを提供することで、より細かい制御が得られます。これらは、他の入力に基づいて対応する因数分解が呼び出された場合にのみ使用されます。`alg_lq`、`alg_polar`、または `alg_svd` が NamedTuples の場合、デフォルトのアルゴリズムが `select_algorithm` で選択され、NamedTuple がそのアルゴリズムへのキーワード引数として渡されます。`alg_lq` のデフォルトは `(; positive=true)` であり、デフォルトで正の LQ 分解が使用されます。

!!! note
    バン方法 `right_orth!` は、出力構造をオプションで受け入れ、入力行列 `A` を破壊する可能性があります。常に関数の戻り値を使用してください。提供された `CVᴴ` を出力として使用できない場合があるためです。


他にも [`left_orth(!)`](@ref left_orth)、[`left_null(!)`](@ref left_null)、[`right_null(!)`](@ref right_null) を参照してください。
