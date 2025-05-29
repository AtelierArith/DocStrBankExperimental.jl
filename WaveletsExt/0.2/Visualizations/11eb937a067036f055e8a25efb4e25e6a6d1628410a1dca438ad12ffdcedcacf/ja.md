```
wiggle(args...[; kwargs...])
wiggle(plt, args...[; kwargs...])
```

一連の陰影のあるウィグルをプロットします。

# 引数

  * `plt::Plots.Plot`: 陰影のあるウィグルをプロットするための入力プロット。
  * `args...`: `wiggle`の追加の位置引数。[`wiggle!`](@ref)を参照してください。

# キーワード引数

  * `kwargs...`: `wiggle`のキーワード引数。[`wiggle!`](@ref)を参照してください。

# 戻り値

`::Plots.Plot`: 現在のプロットオブジェクトの上に陰影のあるウィグル。

# 例

```julia
using Plots, WaveletsExt

# ランダム信号を生成
x = randn(16, 5)

# ----- ウィグルを構築 -----
# メソッド 1
wiggle(x)

# メソッド 2
p = Plot()
wiggle(p, x)
```

翻訳者: Nicholas Hausch – MATLABファイルは斉藤直樹によって提供されました。以前のMATLABバージョンの貢献者は、Anthony K. Booer (SLB) と Bradley Marchand (NSWC-PC) です。

改訂者: 斉藤直樹, 2018年2月5日。最新のJuliaバージョンの互換性のために、Zeng Fung Liewによって維持されています。

**関連情報:** [`wiggle!`](@ref)
