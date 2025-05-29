```julia
project!(
    state,
    pauli::QuantumClifford.PauliOperator;
    keep_result,
    phases
) -> Tuple{QuantumClifford.MixedStabilizer, Int64, Any}

```

パウリ演算子の二つの固有空間に対する安定器の状態を投影します。

入力が有効な安定器であることを前提としています。投影はその安定器に対してインプレースで行われ、投影演算子は変更されません。

返されるものは

  * 標準形ではないかもしれない安定器
  * 非可換演算子があった行のインデックス（その行は現在`pauli`と等しくなっており、その位相は更新されず、忠実な測定シミュレーションのためにはユーザーによってランダム化する必要があります）
  * そして、非可換演算子がなかった場合の投影の結果（そうでない場合は`nothing`）

`keep_result==false`の場合、反交換の際の投影の結果は計算されず、標準化操作が省かれます。この標準化操作は、潜在的に立方体の複雑さを持つ唯一のものです。他の計算は二次の複雑さです。

複数キュービットのパウリ演算子の代わりに単一キュービットを測定する必要がある場合、より高速な[`projectX!`](@ref)、[`projectY!`](@ref)、および[`projectZ!`](@ref)が利用可能です。

より少ないボイラープレートと位相の自動ランダム化を使用するには、[`projectrand!`](@ref)を使用してください。

以下は、エンタングルメントを破壊する投影の例です：

```jldoctest
julia> ghz = S"XXXX
               ZZII
               IZZI
               IIZZ";


julia> canonicalize!(ghz)
+ XXXX
+ Z__Z
+ _Z_Z
+ __ZZ

julia> state, anticom_index, result = project!(ghz, P"ZIII");


julia> state
+ Z___
+ Z__Z
+ _Z_Z
+ __ZZ

julia> canonicalize!(state)
+ Z___
+ _Z__
+ __Z_
+ ___Z

julia> anticom_index, result
(1, nothing)
```

安定器状態と一致する投影の例です。

```jldoctest
julia> s = S"ZII
             IXI
             IIY";


julia> canonicalize!(s)
+ _X_
+ __Y
+ Z__

julia> state, anticom_index, result = project!(s, P"-ZII");


julia> state
+ _X_
+ __Y
+ Z__

julia> anticom_index, result
(0, 0x02)
```

最良の選択ではありませんが、`Stabilizer`は不完全なタブローを提供することによって混合状態に使用できます。その場合、提供された安定器演算子によって生成できない演算子に対して投影を試みることが可能です。その場合、`anticom_index==rank`となり、`result===nothing`となります。ここで、`rank`はタブローの新しいランクで、初期タブローの行数よりも1つ多いです。ただし、`keep_result`が`false`に設定されている場合、`anticom_index`はゼロのままになります。

```jldoctest
julia> s = S"XZI
             IZI";


julia> project!(s, P"IIX")[1]
+ X__
+ _Z_
```

[`MixedStabilizer`](@ref)を使用していれば、プロジェクターを安定器のリストに追加していたでしょう。

```jldoctest
julia> s = one(MixedStabilizer, 2, 3)
+ Z__
+ _Z_

julia> project!(s, P"IIX")[1]
+ Z__
+ _Z_
+ __X
```

しかし、[`MixedDestabilizer`](@ref)は、`*Stabilizer`の$\mathcal{O}(n^3)$の複雑さの代わりに$\mathcal{O}(n^2)$の複雑さを持つため、さらに良い選択です。

```jldoctest
julia> s = one(MixedDestabilizer, 2, 3)
𝒟ℯ𝓈𝓉𝒶𝒷
+ X__
+ _X_
𝒳ₗ━━━
+ __X
𝒮𝓉𝒶𝒷━
+ Z__
+ _Z_
𝒵ₗ━━━
+ __Z

julia> project!(s, P"IIX")[1]
𝒟ℯ𝓈𝓉𝒶𝒷
+ X__
+ _X_
+ __Z
𝒮𝓉𝒶𝒷━
+ Z__
+ _Z_
+ __X
```

詳細については、ドキュメントの「データ構造の選択」セクションを参照してください。

参照：[`projectX!`](@ref)、[`projectY!`](@ref)、[`projectZ!`](@ref)、[`projectrand!`](@ref)
