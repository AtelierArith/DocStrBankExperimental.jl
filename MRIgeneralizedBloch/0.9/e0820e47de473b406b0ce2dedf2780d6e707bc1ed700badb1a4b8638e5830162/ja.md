```
qM = fit_gBloch(data, α, TRF, TR;
    reM0 = (-Inf,   1,  Inf),
    imM0 = (-Inf,   0,  Inf),
    m0s  = (   0, 0.2,    1),
    R1f  = (   0, 0.3,  Inf),
    R2f  = (   0,  15,  Inf),
    Rx   = (   0,  20,  Inf),
    R1s  = (   0,   3,  Inf),
    T2s  = (8e-6,1e-5,12e-6),
    ω0   = (-Inf,   0,  Inf),
    B1   = (   0,   1,  1.5),
    R1a  = (   0, 0.7,  Inf),
    u=1,
    fit_apparentR1=false,
    show_trace=false,
    maxIter=100,
    R2slT = precompute_R2sl(TRF_min=minimum(TRF), TRF_max=maximum(TRF), T2s_min=minimum(T2s), T2s_max=maximum(T2s), ω1_max=maximum(α ./ TRF), B1_max=maximum(B1)),
    )
```

RFパルスの列とバランスの取れた勾配モーメントに対して一般化されたBlochモデルを`data`にフィットさせます。

# 引数

  * `data::Vector{Number}`: 測定データポイントの配列、時間領域または圧縮領域（cf. `u`）のいずれか
  * `α::Vector{Real}`: ラジアン単位のフリップ角の配列; 各RFパターンをシミュレートし、各シミュレーションの信号を連結する`Vector{Vector{Real}}`でも可能
  * `TRF::Vector{Real}`: RFパルスの持続時間の配列（秒単位）（または`α::Vector{Vector{Real}}`の場合は`Vector{Vector{Real}}`）
  * `TR::Real`: 繰り返し時間（秒単位）
  * `ω0::Real`: オフ共鳴周波数（rad/s）

# オプションのキーワード引数:

  * `reM0::Union{Real, Tuple{Real, Real, Real}}`: `M0`の実部; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `imM0::Union{Real, Tuple{Real, Real, Real}}`: `M0`の虚部; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `m0s::Union{Real, Tuple{Real, Real, Real}}`: 半固体プールの分数サイズ（0から1の範囲であるべき）; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `R1f::Union{Real, Tuple{Real, Real, Real}}`: 自由プールの縦緩和率（1/s）; `fit_apparentR1=false`と組み合わせてのみ使用; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `R2f::Union{Real, Tuple{Real, Real, Real}}`: 自由プールの横緩和率（1/s）; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `Rx::Union{Real, Tuple{Real, Real, Real}}`: 2つのスピンプール間の交換率（1/s）; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `R1s::Union{Real, Tuple{Real, Real, Real}}`: 半固体プールの縦緩和率（1/s）; `fit_apparentR1=false`と組み合わせてのみ使用; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `T2s::Union{Real, Tuple{Real, Real, Real}}`: 半固体プールの横緩和時間（s）; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `ω0::Union{Real, Tuple{Real, Real, Real}}`: オフ共鳴周波数（rad/s）; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `B1::Union{Real, Tuple{Real, Real, Real}}`: 正規化された送信B1フィールド、すなわちB1 = 1は適切にキャリブレーションされたB1フィールドに対応; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `R1a::Union{Real, Tuple{Real, Real, Real}}`: 見かけの縦緩和率（1/s）; `fit_apparentR1=true`と組み合わせてのみ使用; 固定値としての`Real`または要素`(min, start, max)`を持つ`Tuple`としてのフィット制限
  * `u::Union{Number, Matrix}`: シミュレートされた時系列を係数の系列に変換する圧縮行列。デフォルトでは`1`に設定され、時間領域でのフィッティングを有効にします
  * `fit_apparentR1::Bool`: `R1f`と`R1s`を別々にフィットするか（`false`; デフォルト）、見かけの`R1a = R1f = R1s`（`true`）に切り替えます
  * `show_trace::Bool`: 最適化中に出力を印刷します; `default=false`
  * `maxIter::Int`: 最大反復回数; `default=100`
  * `R2slT::NTuple{3, Function}`: 3つの関数のタプル: R2sl(TRF, ω1, B1, T2s)、dR2sldB1(TRF, ω1, B1, T2s)、およびR2sldT2s(TRF, ω1, B1, T2s)。デフォルトでは[`precompute_R2sl`](@ref)で生成されます

# 例

c.f. [非線形最小二乗フィッティング](@ref)
