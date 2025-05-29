```
tickline(startpos, finishpos;
    startnumber         = 0,
    finishnumber        = 1,
    major               = 1,
    minor               = 0,
    major_tick_function = nothing,
    minor_tick_function = nothing,
    rounding            = 2,
    axis                = true, # 線を描画するか？
    log                 = false,
    vertices            = false # ポイントだけを返す
    )
```

ティック付きの線を描画します。`major`は開始点と終了点の間に必要なティックの数です。したがって、`1`は線を半分に分割します。`minor`は各メジャーティックの間のティックの数です。

## 例

```julia
tickline(Point(0, 0), Point(100, 0))
tickline(Point(0, 0), Point(100, 0), major = 4)
majorticks, minorticks = tickline(Point(0, 0), Point(100, 0), axis=false)
```

## カスタムティック

カスタムティックを作成するための関数を提供します。カスタムティック関数は次のような引数を持つ必要があります。

```julia
function mtick(n, pos;
        startnumber         = 0,
        finishnumber        = 1,
        nticks = 1)
        ...
```

および

```julia
function mntick(n, pos;
        startnumber        = 0,
        finishnumber       = 1,
        nticks             = 1,
        majorticklocations = [])
        ...
```

例えば：

```julia
tickline(O - (300, 0), Point(300, 0),
    startnumber  = -10,
    finishnumber = 10,
    minor        = 0,
    major        = 4,
    axis         = false,
    major_tick_function = (n, pos;
        startnumber=30, finishnumber=40, nticks=10) -> begin
        @layer begin
            translate(pos)
            ticklength = get_fontsize()
            line(O, O + polar(ticklength, 3π/2), :stroke)
            k = rescale(n, 0, nticks - 1, startnumber, finishnumber)
            ticklength = get_fontsize() * 1.3
            text("$(round(k, digits=2))",
                O + (0, ticklength),
                halign=:center,
                valign=:middle,
                angle = -getrotation())
        end
    end)
```
