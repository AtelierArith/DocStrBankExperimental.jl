```
extrapolate!(fh::AbstractVector; power=1, atol=0, rtol=0, maxeval=typemax(Int), breaktol=Inf)
```

`extrapolate(fh)`と同様に、`(f(h), h)`タプルの配列`fh`（`|h|`が減少する順序で）に対してリチャードソン外挿を実行しますが、中間計算で配列`fh`をインプレースで上書きします。

（したがって、配列`fh`は`Tuple{T,H}`値のベクターでなければならず、ここで`H<:Number`は`h`の型であり、`T`は外挿された`f(0)`の**結果**の型です。この`T`は浮動小数点型である必要があり、すなわち、外挿している関数がすでに浮動小数点値でない場合、`fh`は`float(f(h))`を含む必要があります。）
