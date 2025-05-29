```
multispec(S1; <キーワード引数>)
```

マルチバリアント版のmultispec呼び出しで、データは行列の列にあります...

# 引数

  * `S1::Matrix{T} where T<:Float64`: 最初の時系列を含むベクトル
  * `outp::Symbol`: 出力は:coh（コヒーレンス）、:justspeccs（スペクトルのみを計算）、または:cross（クロススペクトル）のいずれかです
  * `NW::Float64 = 4.0`: 推定の時間帯域幅の積
  * `K::Int64 = 6`: スレピアンテーパーの数、2*NW以下でなければなりません
  * `dt::Float64`: 時間単位でのサンプリングレート
  * `ctr::Bool`: マルチテーパースペクトルを計算する前に平均を除去するかどうか
  * `pad::Float64 = 1.0`: シリーズをパディングするための係数、すなわちスペクトルの長さはパッドと時系列の長さの積になります。
  * `dpVec::Union{Matrix{Float64},Nothing} = nothing`: 事前に計算されたdpssの行列
  * `guts::Bool = false`: 出力構造体に固有係数を返すかどうか
  * `a_weight::Bool = true`: スペクトルを適応的に重み付けするかどうか
  * `jk::Bool = false`: ジャックナイフされた信頼区間を計算する
  * `Ftest:Bool = false`: 線成分のF検定を計算する
  * `Tsq::Union{Vector{Int64},Vector{Vector{Int64}},Nothing} = nothing`: 複数の線成分のためのT二乗検定を計算する周波数インデックス。デフォルトはなし。
  * `alph::Float64 = 0.05`: T二乗検定の有意性カットオフ

...

...

# 出力

  * `Tuple{Vector{MTSpectrum},Vector{P},Union{Float64,Vector{Float64}}} where P = Union{MTCoherence,MTSpectrum}`

スペクトル、コヒーレンスまたはクロススペクトル、およびT二乗検定のp値を含む構造体。中間引数の出力は`outp`入力の選択に依存します。...

参照: [`dpss_tapers`](@ref), [`MTSpectrum`](@ref), [`mdmultispec`](@ref), [`mdslepian`](@ref)
