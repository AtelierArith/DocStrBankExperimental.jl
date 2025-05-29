```
slidingwindow(data; size, stride=1, obsdim=nothing) -> SlidingWindow
```

`data`のベクトルのようなビューを返します。各要素は、`size`の隣接する観測値の固定サイズの「ウィンドウ」です。

`stride`は、各隣接ウィンドウの開始要素間の距離を指定します。デフォルト値は1です。出力には完全なウィンドウのみが含まれるため、余分な観測値がビューから省略される可能性があることに注意してください。

`obsdim`は、観測値がインデックス付けされる次元を指定します（例：配列などのデータ型でサポートされています）。デフォルトでは、観測値はデータの最後の次元に沿ってインデックス付けされます。`obsdim`が指定されると、それは`obsview`に渡され、その次元に沿ったデータのビューを取得します。

ウィンドウは構築時に具現化されないことに注意してください。実際にウィンドウのデータのコピーを取得するには、インデックス付けまたは[`getobs`](@ref)を使用します。

データにインデックス付けする際は、`getobs(data, idxs)`としてアクセスされ、`idxs`は適切なインデックスの範囲です。

# 例

```jldoctest
julia> s = slidingwindow(11:30, size=6)
slidingwindow(20-element UnitRange{Int64}, size=6, stride=1)

julia> s[1]  # == getobs(data, 1:6)
11:16

julia> s[2]  # == getobs(data, 2:7)
12:17
```

オプションのパラメータ`stride`は、各隣接ウィンドウの開始要素間の距離を指定するために使用できます。デフォルトでは、ストライドは1に等しいです。

```jldoctest
julia> s = slidingwindow(11:30, size=6, stride=3)
slidingwindow(20-element UnitRange{Int64}, size=6, stride=3)

julia> for w in s; println(w); end
11:16
14:19
17:22
20:25
23:28
```
