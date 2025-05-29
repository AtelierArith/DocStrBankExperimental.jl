# StatsPlots.errorline(x, y, arg):

```
入力を解析して、[`ribbons`] (https://ggplot2.tidyverse.org/reference/geom_ribbon.html)、スティックエラーバー (https://www.mathworks.com/help/matlab/ref/errorbar.html)、またはプルーム (https://stackoverflow.com/questions/65510619/how-to-prepare-my-data-for-plume-plots) プロットを簡単に作成できる関数で、エラータイプとNaNの処理を簡単に制御できるようにします。
```

# 入力: デフォルト値は *s で示されています

```
x (ベクトル, 単位範囲) - 各yポイントのx軸に沿った値

y (行列 [x, 繰り返し, グループ]) - xに対するy軸に沿った値。最初の次元はxの長さと等しくなければなりません。
    2番目の次元は繰り返し観測として扱われ、この次元に沿ってエラーが計算されます。行列に3次元目がある場合、これは新しいグループとして扱われます。

error_style (`Symbol` - *:ribbon*, :stick, :plume) - リボンスタイルまたはスティックスタイルのエラー表現を使用するかどうかを決定します。

centertype (シンボル - *:mean* または :median) - 各x値でyの中心値を表すために使用するアプローチ。

errortype (シンボル - *:std*, :sem, :percentile) - 各x値でyの分布を示すために使用するエラーメトリック。

percentiles (Vector{Int64} *[25, 75]*) - errortype === :percentileを使用する場合、境界として使用するパーセンタイル。

groupcolor (シンボル, RGB, シンボルまたはRGBのベクトル) - 各グループの色を宣言します。値が渡されない場合は、デフォルトのカラースキームを使用します。1つの値が与えられた場合、すべてのグループにその色を使用します。複数の色が与えられた場合、各グループに異なる色を使用します。

secondarycolor (`Symbol`, `RGB`, `:matched` - *:Gray60*) - スティックモードを使用する場合、スティックの色を設定できます。
    `:matched`が与えられた場合、スティックの色はメインラインの色と一致します。

secondarylinealpha (float *.1*) - プルームラインのアルファ値。

numsecondarylines (int *100*) - 中央線の後ろにプロットするプルームラインの数。

stickwidth (Float64 *.01*) - エラースティックの水平部分がx軸のどれだけを占めるべきか。
```

# 例

```julia
x = 1:10
y = fill(NaN, 10, 100, 3)
for i = axes(y,3)
    y[:,:,i] = collect(1:2:20) .+ rand(10,100).*5 .* collect(1:2:20) .+ rand()*100
end

y = reshape(1:100, 10, 10);
errorline(1:10, y)
```
