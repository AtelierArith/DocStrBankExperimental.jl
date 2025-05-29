```julia
function taperinfo(taper::Taper)
```

[Taper](@ref)オブジェクトにカプセル化されたテーパリングウィンドウの名前を文字列として返します。

スレピアンの離散プロレート球面系列（dpss）のみ、そのパラメータ、すなわち、$α$（ハーフバンド幅）と$n$（ウィンドウの数）が括弧内に報告されます。

**例**:

```julia
H=taper(hamming, 128*8)
taperinfo(H)

H=slepians(128, 128*8, 2)
taperinfo(H)
```
