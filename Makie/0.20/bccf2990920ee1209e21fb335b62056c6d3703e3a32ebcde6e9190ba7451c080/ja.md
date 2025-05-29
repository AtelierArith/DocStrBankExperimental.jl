```
qqplot(x, y; kwargs...)
```

2つの分布の分位数を比較するQ-Qプロットを描画します。`y`はサンプルのリスト、すなわち`AbstractVector{<:Real}`でなければならず、`x`は次のいずれかであることができます。

  * サンプルのリスト
  * 抽象分布、例：`Normal(0, 1)`
  * 分布タイプ、例：`Normal`

最後の場合、分布タイプはデータ`y`にフィットされます。

属性`qqline`（デフォルトは`:none`）は、Q-Qプロットのフィットラインを計算する方法を決定します。可能な値は次のとおりです。

  * `:identity`はアイデンティティラインを描画します。
  * `:fit`は分位数ペアの最小二乗ラインフィットを計算します。
  * `:fitrobust`は分布の第一四分位数と第三四分位数を通るラインを計算します。
  * `:none`はラインの描画を省略します。

一般的に、`qqline = :identity`は`x`と`y`が同じ分布に従うかどうかを確認するのに役立ち、`qqline = :fit`および`qqline = :fitrobust`は`y`の分布が`x`の分布からアフィン変換を介して得られるかどうかを確認するのに役立ちます。

グラフィカル属性は次のとおりです。

  * `color`はラインとマーカーの色を制御します（`markercolor`が指定されていない場合）
  * `linestyle`
  * `linewidth`
  * `markercolor`
  * `strokecolor`
  * `strokewidth`
  * `marker`
  * `markersize`

```
