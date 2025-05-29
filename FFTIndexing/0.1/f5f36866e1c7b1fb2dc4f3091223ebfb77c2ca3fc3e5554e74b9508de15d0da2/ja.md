```
FFTIndices{D} <: AbstractArray{FFTIndex{D},D}
```

FFTインデックスに対応するCartesianIndicesの範囲を定義する反復可能なオブジェクトです。これを使用して、Cartesian配列インデックスをFFTビンインデックスに変換したり、その逆を行ったりできます。

インデックス可能なオブジェクトのすべての有効なインデックスに対応する`FFTIndex{D}`オブジェクトの配列です。

出力は、その次元のナイキスト周波数以上の周波数が負であるという慣例を使用しており、`FFTW.fftfreq`の出力と一致します。

# 例

```
julia> FFTIndices(4)
4-element FFTIndices{1}:
 FFTIndex(0,)
 FFTIndex(1,)
 FFTIndex(-2,)
 FFTIndex(-1,)

julia> FFTIndices(3, 3)
3×3 FFTIndices{2}:
 FFTIndex(0, 0)   FFTIndex(0, 1)   FFTIndex(0, -1)
 FFTIndex(1, 0)   FFTIndex(1, 1)   FFTIndex(1, -1)
 FFTIndex(-1, 0)  FFTIndex(-1, 1)  FFTIndex(-1, -1)
```
