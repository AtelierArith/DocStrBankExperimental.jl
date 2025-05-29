```
ParamBox{T, V, F<:Function} <: DifferentiableParameter{T, ParamBox}
```

微分を可能にするパラメータコンテナ。

≡≡≡ フィールド ≡≡≡

`data::Array{Pair{Array{T, 0}, Symbol}, 0}`: `ParamBox`に格納された値のコンテナとシンボルの`Pair`の形での入力変数データのコンテナ。入力変数の値には`[]`構文でアクセスでき、例えば`pb::ParamBox{T}`の場合、`pb[] = newVal`という構文を使って変更できます。ここで`newVal`は新しい値で、型`T`に変換可能である必要があります。

`map::Union{F,`[`DI`](@ref)`{F}}`: 同じドメイン内での入力変数の値（すなわち入力値）のマッピング（`.map(::T)->T`）。結果（すなわち出力変数の値、または「出力値」）には`()`構文でアクセスできます。

`canDiff::Array{Bool, 0}`: 微分プロセスにおいて出力変数が入力変数に対して「マーク」されているかどうかの指標。言い換えれば、`ParamBox`によって表される出力変数が従属変数として扱われるか独立変数として扱われるかを決定します。

`index::Array{Union{Int, Nothing}, 0}`: `ParamBox`に割り当てられた追加のインデックス。

≡≡≡ 初期化メソッド ≡≡≡

```
ParamBox(inVar::Union{T, Array{T, 0}}, outSym::Symbol=:undef, 
         inSym::Symbol=Symbol(IVsymSuffix, outSym); 
         index::Union{Int, Nothing}=nothing, canDiff::Bool=false) where {T} -> 
ParamBox{T, outSym, typeof(Quiqbox.itself)}

ParamBox(inVar::Union{T, Array{T, 0}}, outSym::Symbol, mapFunction::Function, 
         inSym::Symbol=Symbol(IVsymSuffix, outSym); 
         index::Union{Int, Nothing}=nothing, canDiff::Bool=true) where {T} -> 
ParamBox{T, outSym}
```

=== 位置引数 ===

`inVar::Union{T, Array{T, 0}}`: 保存される入力変数の値またはコンテナ。後者が`data`の型である場合、`.data[]`をコピーなしで直接構築するために使用されます。

`outSym::Symbol`: 構築された`ParamBox`によって表される出力変数のシンボル。これは構築された`ParamBox`の型パラメータ`V`に等しいです。

`inSym::Symbol`: 構築された`ParamBox`が保持する入力変数のシンボル。

`mapFunction::Function`: 入力変数のマッピング（`mapFunction(::T)->T`）で、フィールド`.map`に割り当てられます。`mapFunction`が提供されない場合、`.map`は入力変数を同一値の出力変数にマッピングする[`itself`](@ref)に設定されます。

=== キーワード引数 ===

`index::Union{Int, Nothing}`: 構築された`ParamBox`のインデックス。微分以外の特定のアプリケーションのために`ParamBox`のインデックスを利用する予定がない限り、デフォルト値のままにしておくべきです。

`canDiff::Bool`: 出力変数が入力変数に対して「微分可能」としてマークされているかどうかを決定します。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> ParamBox(1.0)
ParamBox{Float64, :undef, …}{0}[∂][undef]⟦=⟧[1.0]

julia> ParamBox(1.0, :a)
ParamBox{Float64, :a, …}{0}[∂][a]⟦=⟧[1.0]

julia> ParamBox(1.0, :a, abs)
ParamBox{Float64, :a, …}{1}[𝛛][x_a]⟦→⟧[1.0]
```

**注意 1:** 印刷された情報の"`[∂][IV]`"マーカーは、`ParamBox`に結びついた独立変数の微分可能性と名前（適用された場合は割り当てられたインデックスを持つシンボル）を示します。`ParamBox`が非微分可能としてマークされている場合、"`[∂]`"は灰色で、`IV`は出力変数の名前に対応します。`ParamBox`が微分可能としてマークされている場合、"`[∂]`"は緑の"`[𝛛]`"になり、`IV`は保存された入力変数の名前に対応します。

**注意 2:** `ParamBox`の出力変数は通常、パラメータ関数（例：ハートリー–フォックエネルギー）を微分するために使用されます。しかし、`ParamBox`が微分可能としてマークされている場合、保存された入力変数に関しても微分を計算できます。
