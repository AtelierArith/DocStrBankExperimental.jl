```
struct SimpleCSAFilter <: AbstractRadIIRFilter
```

抵抗性リセットを持つ電荷感度プリアンプの電流信号応答をシミュレートし、出力は電荷信号です。

これは次の合成に相当します。

```julia
CRFilter(cr = tau_decay) ∘
Integrator(gain = gain) ∘
RCFilter(rc = tau_rise)
```

そして、単一の `BiquadFilter` にマッピングされます。

このフィルターには逆がありますが、`tau_rise` がゼロでない場合、追加のノイズが存在すると逆は非常に不安定です（RCフィルターの逆はノイズの下で不安定です）。たとえ `tau_rise` がゼロであっても、逆はノイズを増幅します（微分するため）、したがって実際のアプリケーションで信号をデコンボルーションする際には非常に注意して使用する必要があります。

コンストラクタ：

  * `SimpleCSAFilter(fields...)`

フィールド：

  * `tau_rise::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 上昇時間定数
  * `tau_decay::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 減衰時間定数
  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: ゲイン
