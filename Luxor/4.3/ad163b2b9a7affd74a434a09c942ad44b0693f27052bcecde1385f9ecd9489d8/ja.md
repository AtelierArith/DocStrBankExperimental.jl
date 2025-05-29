```
pathtobezierpaths(
    ; flat=true)
```

現在のCairoパス（1つ以上のパスで構成される可能性があります）を、各々がBezierPathSegmentsの配列であるBezierパスの配列に変換します。各パスセグメントは4つのポイントのタプルです。直線は、制御点が端点と同じになるように設定されたBezierセグメントに変換されます。

`flat`がtrueの場合、`getpath()`の代わりに`getpathflat()`を使用します。

# 例

このコードはBezierPathSegmentsを描画し、制御点を「ハンドル」として表示します。これはベクター編集プログラムのようなものです。

```julia
@svg begin
    fontface("MyanmarMN-Bold")
    st = "goo"
    thefontsize = 100
    fontsize(thefontsize)
    sethue("red")
    fontsize(thefontsize)
    textpath(st)
    nbps = pathtobezierpaths()
    for nbp in nbps
        setline(.15)
        sethue("grey50")
        drawbezierpath(nbp, :stroke)
        for p in nbp
            sethue("red")
            circle(p[2], 0.16, :fill)
            circle(p[3], 0.16, :fill)
            line(p[2], p[1], :stroke)
            line(p[3], p[4], :stroke)
            if p[1] != p[4]
                sethue("black")
                circle(p[1], 0.26, :fill)
                circle(p[4], 0.26, :fill)
            end
        end
    end
end
```
