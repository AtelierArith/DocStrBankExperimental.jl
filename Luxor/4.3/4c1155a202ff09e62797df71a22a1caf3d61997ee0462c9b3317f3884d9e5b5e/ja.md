```
barchart(values;
        boundingbox = BoundingBox(O + (-250, -120), O + (250, 120)),
        bargap=10,
        margin = 5,
        border=false,
        labels=false,
        labelfunction = (values, i, lowpos, highpos, barwidth, scaledvalue) -> begin
                label(string(values[i]), :n, highpos, offset=10)
          end,
        barfunction =  (values, i, lowpos, highpos, barwidth, scaledvalue) -> begin
            @layer begin
                setline(barwidth)
                line(lowpos, highpos, :stroke)
            end
          end)
```

`values` 配列の各値の高さを持つ棒グラフを描画します。棒はバウンディングボックスに収まるようにスケーリングされます。

キーワード `labels=true` が指定されている場合、テキストラベルが描画されます。

# 拡張ヘルプ

この関数は、各バーの底部中央の点のベクトルを返します。

棒グラフとしてフィボナッチ数列を描画します：

```julia
fib(n) = n > 2 ? fib(n - 1) + fib(n - 2) : 1
fibs = fib.(1:15)
@draw begin
    fontsize(12)
    barchart(fibs, labels=true)
end
```

テキストとバーの描画を制御するために、端点を処理する関数を定義します：

`mybarfunction(values, i, lowpos, highpos, barwidth, scaledvalue)`

`mylabelfunction(values, i, lowpos, highpos, barwidth, scaledvalue)`

そして、このように渡します：

```julia
barchart(vals, barfunction=mybarfunction)
barchart(vals, labelfunction=mylabelfunction)
```

```julia
function myprologfunction(values, basepoint, minbarrange, maxbarrange, barchartheight)
    @layer begin
        setline(0.2)
        for i in 0:10:maximum(values)
            rule(boxbottomcenter(basepoint) + (0, -(rescale(i, minbarrange, maxbarrange) * barchartheight)))
        end
    end
end
```
