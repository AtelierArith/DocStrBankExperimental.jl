```julia
FunctionOperator(op, input; ...)
FunctionOperator(
    op,
    input,
    output;
    op_adjoint,
    op_inverse,
    op_adjoint_inverse,
    p,
    t,
    accepted_kwargs,
    T,
    isinplace,
    outofplace,
    has_mul5,
    isconstant,
    islinear,
    isconvertible,
    batch,
    ifcache,
    cache,
    opnorm,
    issymmetric,
    ishermitian,
    isposdef,
    kwargs...
)

```

呼び出し可能なオブジェクト `op` を `AbstractSciMLOperator` 内にラップします。`op` は次のシグネチャを持つと仮定されます。

```
op(u, p, t; <accepted_kwargs>) -> v
```

または

```
op(v, u, p, t; <accepted_kwargs>) -> [vを変更]
```

そしてオプションで

```
op(v, u, p, t, α, β; <accepted_kwargs>) -> [vを変更]
```

ここで `u`、`v` は `AbstractArray`、`p` はパラメータオブジェクト、`t`、`α`、`β` はスカラーです。最初のシグネチャは `Base.*` を使用して演算子を適用することに対応し、残りの2つはそれぞれ3引数および5引数の `mul!` に対応します。

`input` と `output` のプロトタイプ `AbstractArray` が必要で、演算子の特性（`eltype`、`size` など）を決定し、キャッシュを事前に割り当てるために使用されます。`output` 配列が提供されない場合、出力は入力と同じ型で共有されると仮定されます。

# キーワード引数

キーワード引数は、随伴評価関数 `op_adjoint`、逆関数 `op_inverse`、および随伴逆関数 `adjoint_inverse` を渡すために使用されます。すべては同じ呼び出しシグネチャと以下の特性を持つと仮定されます。

## 特性

キーワード引数は演算子の特性を設定するために使用され、`op`、`op_adjoint`、`op_inverse`、`op_adjoint_inverse` の間で均一であると仮定されます。

  * `p` - 評価中に演算子に渡されるパラメータ構造体のプロトタイプ、すなわち `L(u, p, t)`。値が提供されない場合、`p` は `nothing` に設定されます。
  * `t` - 評価中に演算子に渡されるスカラー時間変数のプロトタイプ。値が提供されない場合、`t` は `zero(T)` に設定されます。
  * `accepted_kwargs` - `op*` および `update_coefficients[!]` によって受け入れられるキーワード引数に対応する `Symbol` の `Tuple`。たとえば、`op` が `scale` というキーワード引数を受け入れる場合、`op(u, p, t; scale)` のように、`accepted_kwargs = (:scale,)` となります。
  * `T` - 演算子の `eltype`。値が提供されない場合、コンストラクタは `input` と `output` の型から値を推測します。
  * `isinplace` - 演算子がインプレース割り当てで変更可能な方法で使用できる場合は `true`。値が提供されない場合、この特性は推測されます。
  * `outofplace` - 演算子がインプレース割り当てで非変更的な方法で使用できる場合は `true`。値が提供されない場合、この特性は推測されます。
  * `has_mul5` - 演算子がシグネチャ `op(v, u, p, t, α, β; <accepted_kwargs>)` を介して5引数の `mul!` を提供する場合は `true`。値が提供されない場合、この特性は推測されます。
  * `isconstant` - 演算子が定数であり、演算子評価中に `update_coefficients[!]` を介して更新する必要がない場合は `true`。
  * `islinear` - 演算子が線形である場合は `true`。デフォルトは `false`。
  * `isconvertible` - 安価な `convert(AbstractMatrix, L.op)` メソッドが利用可能な場合は `true`。デフォルトは `false`。
  * `batch` - 入力/出力配列が行列にスタックされたバッチ列ベクトルで構成されているかどうかを示すブール値。`true` の場合、入力/出力配列は `AbstractVecOrMat` でなければならず、2次元目（バッチ次元）の長さは同じでなければなりません。バッチ次元はサイズ計算には関与しません。たとえば、`batch = true` で、`size(output), size(input) = (M, K), (N, K)` の場合、`FunctionOperator` のサイズは `(M, N)` に設定されます。`batch = false` の場合（デフォルト）、`input`/`output` 配列は任意のサイズであってもよく、`ndims(input) == ndims(output)` であれば、`FunctionOperator` のサイズは `(length(input), length(output))` に設定されます。
  * `ifcache` - コンストラクタでキャッシュ配列を割り当てます。デフォルトは `true`。キャッシュは `cache_operator(L, input, output)` を呼び出すことで後から生成できます。
  * `cache` - インプレース評価用に事前生成されたキャッシュ配列。型と形状は `(similar(input), similar(output),)` である必要があります。値が提供されない場合、コンストラクタはキャッシュを生成します。コンストラクタによるキャッシュ生成は、キーワード引数 `ifcache = false` を設定することで無効にできます。
  * `opnorm` - `op` のノルム。`Number` または関数 `opnorm(p::Integer)` である可能性があります。デフォルトは `nothing`。
  * `issymmetric` - 演算子が線形かつ対称である場合は `true`。デフォルトは `false`。
  * `ishermitian` - 演算子が線形かつエルミートである場合は `true`。デフォルトは `false`。
  * `isposdef` - 演算子が線形かつ正定値である場合は `true`。デフォルトは `false`。
  * `kwargs` - キャッシュ初期化のためのキーワード引数。`accepted_kwargs` が提供されている場合、対応するキーワード引数を渡す必要があります。
