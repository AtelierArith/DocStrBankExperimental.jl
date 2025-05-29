```
SCFconfig{T<:Real, L, MS<:NTuple{L, Val}} <: ImmutableParameter{T, SCFconfig}
```

自己一貫場（SCF）反復設定のための `struct`。

≡≡≡ フィールド ≡≡≡

`method::MS`: 適用される収束方法。これは `NTuple{L, Symbol}` 内の要素として指定され、`SCFconfig` のコンストラクタに位置引数 `methods` として入力されます。各方法に対応する利用可能な設定は、キーワード引数の観点から次の通りです：

| 収束方法                        |              設定               |                 キーワード                  |              範囲/オプション               |               デフォルト |
|:--------------------------- |:-----------------------------:|:--------------------------------------:|:-----------------------------------:| -------------------:|
| `:DD`                       |            ダンピング強度            |             `dampStrength`             |             [`0`, `1`]              |               `0.5` |
| `:DIIS`, `:EDIIS`, `:ADIIS` | サブスペースサイズ; DIIS法ソルバー; リセット閾値¹ | `DIISsize`; `solver`; `resetThreshold` | `1`,`2`...; `:LBFGS`...; `1e-14`... | `10`; `:LBFGS`; N/A |

¹ リセット閾値（`resetThreshold::Real`）は、DIISベースの方法のサブスペースのメモリをクリアし、最新の残差ベクトルを最初の参照としてリセットするタイミングを決定します。リセットは、最新の計算されたエネルギーが、第二最新の計算されたエネルギーと比較して閾値を超えて増加した場合に実行されます。デフォルトでは、閾値は常にSCF計算の数値データ型の機械イプシロンよりもわずかに大きくなります。

### 収束方法

  * `:DD`: フォック行列の直接対角化。
  * `:DIIS`: [反復サブスペースにおける直接反転](https://onlinelibrary.wiley.com/doi/10.1002/jcc.540030413)。
  * `:EDIIS`: [エネルギー-DIIS](https://aip.scitation.org/doi/abs/10.1063/1.1470195)。
  * `:ADIIS`: [拡張ルーサン–ホール（ARH）エネルギー関数に基づくDIIS](https://aip.scitation.org/doi/10.1063/1.3304922)。

### DIIS法ソルバー

  * `:LBFGS`: [ボックス制約付きの制限メモリBFGS](https://github.com/Gnimuc/LBFGSB.jl)。
  * `:LCM`: ラグランジュ乗数ソルバー。
  * `:SPGB`: [ボックス制約付きのスペクトル投影勾配法](https://github.com/m3g/SPGBox.jl)。

`interval::NTuple{L, T}`: 必要な方法の停止（またはスキップ）閾値。最後の閾値はSCF手続きの収束閾値となります。最後の閾値が `NaN` に設定されると、収束検出は行われません。

`methodConfig::NTuple{L, Vector{<:Pair}}`: 各方法の追加キーワード引数を `Pair` の `Tuple` として格納します。

`secondaryConvRatio::NTuple{2, T}`: 主収束指標に対する二次収束基準の比率、すなわちエネルギーの変化（ΔE）：

| 順序  |     シンボル     |           意味           | デフォルト |
|:--- |:------------:|:----------------------:|:-----:|
| 1   | RMS(FDS-SDF) | DIISで定義された誤差行列の二乗平均平方根 |  50   |
| 2   |   RMS(ΔD)    |    密度行列の変化の二乗平均平方根     |  50   |

`oscillateThreshold::T`: 振動収束のための閾値。

≡≡≡ 初期化方法 ≡≡≡

```
SCFconfig(methods::NTuple{L, Symbol}, intervals::NTuple{L, T}, 
          config::Dict{Int, <:AbstractVector{<:Pair}}=Dict(1=>Pair[]); 
          secondaryConvRatio::Union{Real, NTuple{2, Real}}=(50, 50), 
          oscillateThreshold::Real=1.0e-6) where {L, T} -> 
SCFconfig{T, L}
```

`methods` と `intervals` は適用される収束方法とその停止（またはスキップ）閾値です。`config` は、各方法の追加キーワード引数を `Pair` で指定し、キー `i::Int` は `i` 番目の方法のためのもので、指し示す `AbstractVector{<:Pair}` はキーワード引数とその値のペアです。`secondaryConvRatio` が `Real` の場合、すべての二次収束比率の値として割り当てられます。

```
SCFconfig(;threshold::AbstractFloat=(0.001, 1.0e-10), 
           secondaryConvRatio::Union{Real, NTuple{2, Real}}=(50, 50), 
           oscillateThreshold::Real=defaultOscThreshold) -> 
SCFconfig{Float64, 2}
```

`threshold` は、HFconfig() で使用されるデフォルトのSCF設定の停止閾値を新しい値で更新します。言い換えれば、`:1.0e-10` の停止閾値を更新します。

≡≡≡ 例 ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> SCFconfig((:DD, :ADIIS, :DIIS), (1e-4, 1e-12, 1e-13), Dict(2=>[:solver=>:LCM]));

julia> SCFconfig(threshold=1e-8, oscillateThreshold=1e-5)
SCFconfig{Float64, 2, Tuple{Val{:ADIIS}, Val{:DIIS}}}(method, interval=(0.001, 1.0e-8), methodConfig, secondaryConvRatio, oscillateThreshold)
```
