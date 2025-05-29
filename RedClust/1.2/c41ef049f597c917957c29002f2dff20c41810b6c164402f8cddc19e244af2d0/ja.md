```
infodist(a::ClustLabelVector, b::ClustLabelVector;
normalised = true) -> Float64
```

2つのクラスタリング間の情報距離を計算します。情報距離は次のように定義されます。

$$
d_{\mathrm{ID}}(a, b) = \max \{H(A), H(B)\} - I(A, B)
$$

ここで、$A$と$B$はそれぞれ$a$と$b$のクラスタメンバーシップ確率関数、$H$は分布のエントロピーを示し、$I$は2つの分布間の相互情報量を示します。情報距離の範囲は$[0, \log N]$であり、$N$は観測の数です。normalised = trueの場合、結果は範囲$[0, 1]$にスケーリングされます。
