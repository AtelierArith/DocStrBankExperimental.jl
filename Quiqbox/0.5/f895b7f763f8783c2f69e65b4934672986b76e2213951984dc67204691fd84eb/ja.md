```
HFconfig{T1, HFT, F, T2, L, MS} <: ConfigBox{T1, HFconfig, HFT}
```

ハートリー–フォック法の設定のコンテナ。

≡≡≡ フィールド ≡≡≡

`HF::Val{HFT}`: ハートリー–フォック法のタイプ。`HFT`の利用可能な値は:RHF, :UHFです。

`C0::InitialC{T1, HFT, F}`: 標準軌道の係数行列Cの初期推測。`C0`が`HFconfig`のコンストラクタの引数として使用される場合、`sym::Symbol`に設定でき、`sym`の利用可能な値は`：GWH、:Hcore、:SAD`です。また、対応するハートリー–フォック法のタイプのために準備された軌道係数行列の`Tuple`であることもできます。

`SCF::SCFconfig{T2, L, MS}`: SCF反復設定。詳細については、[`SCFconfig`](@ref)を参照してください。

`maxStep::Int`: 反復が収束するかどうかに関係なく許可される最大反復ステップ数。

`earlyStop::Bool`: 収束法の性能が不安定または悪化した場合に、自動的に早期に終了（またはスキップ）するかどうか。

`saveTrace::NTuple{4, Bool}`: すべての反復ステップからの中間情報を出力のフィールド`.temp`に保存（プッシュ）するかどうかを決定します。関連情報のタイプは次のとおりです：

| シーケンス |           情報           | [`HFtempVars`](@ref)の対応するフィールド |
|:-----:|:----------------------:|:------------------------------:|
|   1   |         軌道係数行列         |             `.Cs`              |
|   2   |          密度行列          |     `.Ds`, `.shared.Dtots`     |
|   3   |         フォック行列         |             `.Fs`              |
|   4   | 収束していないハートリー–フォックエネルギー |     `.Es`, `.shared.Etots`     |

≡≡≡ 初期化メソッド ≡≡≡

```
HFconfig(;HF::Union{Symbol, Val}=:RHF, 
          C0::Union{Tuple{AbstractMatrix}, NTuple{2, AbstractMatrix}, 
                    Symbol, Val}=:SAD, 
          SCF::SCFconfig=Quiqbox.SCFconfig{Float64, 2, Tuple{Val{:ADIIS}, Val{:DIIS}}}(method, interval=(0.001, 1.0e-10), methodConfig, secondaryConvRatio, oscillateThreshold), 
          maxStep::Int=150, 
          earlyStop::Bool=true, 
          saveTrace::NTuple{4, Bool}=(false, false, false, true)) -> 
HFconfig
```

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> HFconfig();

julia> HFconfig(HF=:UHF);
```
