```
fit(type::UnfoldModel,d::Vector{Pair},tbl::AbstractDataFrame,data::Array)
fit(type::UnfoldModel,f::FormulaTerm,tbl::AbstractDataFrame,data::Array{T,3},times)
fit(type::UnfoldModel,f::FormulaTerm,tbl::AbstractDataFrame,data::Array{T,2},basisfunction::BasisFunction)
```

デザインマトリックスを生成し、モデルをフィットします。マスユニバリアント（エポック化された時間点ごとに1つのモデル）または時間拡張（線形オーバーラップをモデル化）を使用できます。

## キーワード引数

  * `fit::Bool`（デフォルト: `true`） - デザインマトリックスを構築した後にモデルをフィットします。これを`false`に設定すると、デザインマトリックスを検査したい場合に役立つことがあります。
  * `contrasts::Dict`：（デフォルト: `Dict()`）式に適用されるコントラスト。例: `Dict(:my_condition=>EffectsCoding())`。詳細はこちら: https://juliastats.org/StatsModels.jl/stable/contrasts/
  * `eventcolumn::Union{Symbol,String}`（デフォルト `:event`） - `tbl`内の列で、`d::Vector{Pair}`で定義された基底関数を区別します。
  * `solver::function`：（デフォルト: `solver_default`）。`y=Xb`に使用されるソルバー、例: `(X,y;kwargs...) -> solver_default(X,y;kwargs...)`。より高速で代替のソルバーが利用可能です。オプションのリストについては`solver_predefined`を参照し、オンラインドキュメントの`solver benchmark`を参照してください。GPUを使用するには、`using CUDA`の後にデータを`CuArray`として提供できます。ソルバーを`solver_predef(X,y;solver=:qr)`のように変更してください。lsmr+cudaは通常クラッシュしますが、速度が100倍以上向上する可能性があります。
  * `show_progress::Bool`（デフォルト `true`） - ProgressMeterを介して進行状況を表示します - `solver`に渡されます。
  * `eventfields::Array`：（オプション、デフォルト`[:latency]`）`tbl`内の列名を表すシンボルの配列で、基底関数にイベントごとに渡されます。配列の最初のフィールドは常にサンプル内のイベント開始を定義します。

`Vector[Pairs]`が提供される場合、次のいずれかの構造を持つ必要があります。**デコンボリューション**分析の場合（`Any=>(f,bf)`を使用して、`tbl`のすべての行を1つの基底関数に一致させます）。`data`は連続EEGストリームであると仮定します。`Vector`または`ch x time`の`Matrix`です。

```julia
f1 = @formula(0~1+my_condition)
[
 :A=>(f1,firbasis((-0.1,1),128), # sfreq = 128Hz
 :B=>(f2,firbasis((-3,2),128)
]
```

**マスユニバリアント**分析のためのデコンボリューションなし。`data`はすでにエポックにカットされていると仮定します（`Unfold.epoch`を参照）。*eeglab*標準`ch x time x trials`に従います。

```julia
timesvector = range(-0.1,3,step=1/100)
[
 :A=>(f1,timesvector),
 :B=>(f2,timesvector)
]
```

## 注意事項

  * `type`は、例えば`fit(type::UnfoldLinearModel)`のように直接指定することもできます。自動推論に依存する代わりに。
  * データは、最初の次元が`1`の「チャネル」となるように、1つの次元が欠けている場合に再形成されます。

## 例

マスユニバリアント線形

```julia-repl
julia> data,evts = UnfoldSim.predef_eeg()
julia> data_e,times = Unfold.epoch(data=data,tbl=evts,τ=(-1.,1.9),sfreq=100) # データをエポックにカットします。data_eは現在ch x times x epochです。

julia> f  = @formula 0~1+continuousA+continuousB
julia> model = fit(UnfoldModel,f,evts,data_e,times)
# または:
julia> model = fit(UnfoldModel,[Any=>(f,times)],evts,data_e)
```

時間拡張ユニバリアント線形

```julia-repl
julia> basisfunction = firbasis(τ=(-1,1),sfreq=10)
julia> model = fit(UnfoldModel,f,evts,data,basisfunction)
# または
julia> model = fit(UnfoldModel,[Any=>(f,basisfunction],evts,data)
```
