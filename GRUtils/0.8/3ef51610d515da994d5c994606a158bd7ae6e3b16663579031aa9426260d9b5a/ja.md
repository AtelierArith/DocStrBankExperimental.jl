```
videofile(fun::Function, target, overwrite=false)
videofile(figs::AbstractArray{<:Fig}, target, overwrite=false)
```

関数または図の配列からビデオを作成し、ファイルに保存します。

最初の引数は、ビデオのフレームとして表示される`Figures`の配列、または引数なしで図を描画する関数です（通常は、図が一つずつ作成され描画されるループ）。その関数は、`do`構文を使って`videofile`の呼び出し内で匿名で定義できます（例を参照）。

2番目の引数`target`は、ビデオファイルの名前を持つ文字列であり、その形式はファイルの拡張子によって決まります。サポートされている拡張子は`"webm"`、`"mp4"`または`"mov"`です。

ファイルがすでに存在する場合に`target`の作成を強制するには`overwrite=true`を使用します（そうでない場合、そのようなケースではエラーが発生します）。

# 例

```julia
# サンプルデータでプロットを作成
x = LinRange(0, 800, 100)
y = sind.(x)
plot(x,y)
# X軸をスライドさせるビデオを作成
videofile("sin.mp4") do
  for d = 0:10:440
    xlim(d, d+360)
    draw(gcf())
  end
end
```
