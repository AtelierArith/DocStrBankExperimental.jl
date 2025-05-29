```
POconfig{T, M, CBT<:ConfigBox, TH<:Union{T, NTuple{2, T}}, 
         OM} <: ConfigBox{T, POconfig, M}
```

パラメータ最適化設定の可変コンテナ。

≡≡≡ フィールド ≡≡≡

`method::Val{M}`: 最適化のための目的関数（例：HFエネルギー）を定義するメソッド。Quiqboxからの`M`の利用可能な値は:HFenergy, :DirectRHFenergyです。

`config::CBT`: 選択された`method`の設定。例：`:HFenergy`の場合は[`HFconfig`](@ref)です。

`target::T`: 目的関数のターゲット値。最後のステップの値とターゲット値の差が収束検出に使用されます。`NaN`に設定されている場合、最新のステップの勾配と最新の2ステップの関数値の差が代わりに使用されます。

`threshold::TH`: 目的関数の値の差と勾配のエラー閾値/閾値で、最適化の反復が収束したかどうかを判断します。これが（またはそのいずれかが）`NaN`に設定されている場合、対応する収束検出は行われず、`target`が`NaN`でない場合、勾配の閾値は使用されません。なぜなら、勾配は収束基準の一部ではないからです。

`maxStep::Int`: 収束に関係なく許可される最大反復ステップ数。

`optimizer::F`: 適用されるパラメータ最適化器。デフォルト設定は[`GDconfig`](@ref)`()`です。ユーザーが実装した関数を最適化器として使用するには、次の関数シグネチャを持つ必要があります：

```
optimizer(f::Function, gf::Function, x0::Vector{T}) where {T} -> Function
```

ここで`f`は最小化される目的関数、`gf`は入力値をベクトルとして与えたときに`f`の勾配と返された値の両方を返す関数です。`x0`は初期入力値です。`optimizer`の出力は、これを`optimize!`と呼ぶと、次の関数シグネチャを持つ必要があります：

```
optimize!(x::Vector{T}, gx::Vector{T}, fx::T) where {T}
```

ここで`x`、`gx`、`fx`はそれぞれ1ステップでの入力値、勾配、`f`の返された値です。言い換えれば、`(gx, fx) == (gx, f(x)) == gf(x)`です。これらの引数を受け入れた後、`optimizer`は`x`の要素を更新（すなわち変異させる）し、`f(x)`がより低い返された値を持つようにします。

`saveTrace::NTuple{4, Bool}`: すべての反復ステップからの中間情報を`optimizeParams!`の出力に保存（プッシュ）するかどうかを決定します。関連情報のタイプは次の通りです：

| シーケンス |      対応情報       |
|:-----:|:---------------:|
|   1   |  適用されたメソッドの関数値  |
|   2   |     パラメータ値      |
|   3   | パラメータに関する関数の勾配  |
|   4   | 適用されたメソッドの完全な出力 |

≡≡≡ 初期化メソッド ≡≡≡

```
POconfig(;method::Union{Val{M}, Symbol}=HFenergy, 
          config::ConfigBox=Quiqbox.defaultOFconfigs[method], 
          target::T=NaN, 
          threshold::Union{T, NTuple{2, T}}=(5.0e-8, 5.0e-5), 
          maxStep::Int=200, 
          optimizer::Function=GDconfig()) where 
        {T, M} -> 
POconfig{T, M}
```

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> POconfig();

julia> POconfig(maxStep=100);
```
