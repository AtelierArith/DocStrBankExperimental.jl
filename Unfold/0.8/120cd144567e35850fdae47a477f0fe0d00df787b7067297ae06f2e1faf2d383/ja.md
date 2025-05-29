FIRBasis関数を定義し、各イベントに対して呼び出すことができ、時間拡張された基底カーネルを定義します。

```julia
mutable struct FIRBasis <: Unfold.BasisFunction
```

  * `times`: カーネル出力の行に沿った時間のベクトル（秒単位）
  * `name`: イベントの名前。後でデータフレームの`eventcolumn`にある実際のeventNameであるべきです。
  * `shift_onset`: イベントの開始を何サンプルずらす必要がありますか？この数は、基底関数が定義する「負」の時間点の数によって決まります。
  * `interpolate`: 完全なサンプルにないイベントを線形補間すべきですか？
  * `scale_duration`: カーネルを期間にスケールすべきですか？もしそうなら、どの方法で？

（ヒント: ほとんどのユーザーはfirbasisを呼び出したいと思うでしょう。手動で生成するのではなく。）

# 例

```julia-repl
julia>  b = FIRBasis(range(0,1,length=10),"basisA",-1)
```
