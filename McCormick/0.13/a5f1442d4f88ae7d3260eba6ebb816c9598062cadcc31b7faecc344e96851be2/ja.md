```julia
struct MCNoGrad <: Real
```

`MCNoGrad <: Real` は、RelaxType タグやサブグラディエントを持たない McCormick 構造体です。この構造体は、McCormick 緩和を構築するためのソースコード変換アプローチに使用されます。メソッドの定義と呼び出しは、使用される緩和タイプを指定する必要があります（すなわち） `+(::NS, x::MCNoGrad, y::MCNoGrad)...`。さらに、これに関連するカーネルは、サブグラディエント情報を計算するために必要なすべての中間計算を返しますが、オーバーロード計算は単に `MCNoGrad` オブジェクトを返します。タイポイントのない単変量計算の場合、例えば `log2(::NS, x::MCNoGrad)::MCNoGrad` のようにし、`log2_kernel(::NS, x::MCNoGrad, ::Bool) = (::MCNoGrad, cv_id::Int, cc_id::Int, dcv, dcc)` のようになります。単変量 NS 関数は、従来の規約に従います（MCNoGrad, cv*id, cc*id, dcv, dcc, tp1cv, tp1cc, .... tpncv, tpncc）ここで cv_id は選択されたサブグラディエント（1 = cv, 2 = cc, 3 = 0）であり、dcv と dcc は、評価されている点で定理に従って評価された外部関数の導関数（またはサブ微分の要素）です。tpicv と tpicc は、外部関数のエンベロープを計算するために関連する i 番目のタイポイントです。

  * `cv::Float64`: 凸緩和
  * `cc::Float64`: 凹緩和
  * `Intv::IntervalArithmetic.Interval{Float64}`: 区間境界
  * `cnst::Bool`: ドメイン全体で緩和が定数であるかどうかを示すブール値。区間/定数を境界付けている場合は真。そうでない場合は偽です。計算の過程で `cnst` が変わることがあります。`zero(x)` の場合、`true` であっても `x.cnst` が `false` であることがあります。
