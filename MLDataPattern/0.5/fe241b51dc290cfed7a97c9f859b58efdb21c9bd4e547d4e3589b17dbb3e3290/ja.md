```
slidingwindow(data, size, [stride], [obsdim]) -> UnlabeledSlidingWindow
```

`size` 隣接観測の固定サイズの "ウィンドウ" のベクトルのようなビューを返します。デフォルトでは、これらのウィンドウは重なりません。出力には完全なウィンドウのみが含まれるため、余分な観測がビューから省略される可能性があることに注意してください。

```julia-repl
julia> A = slidingwindow(1:20, 6)
3-element slidingwindow(::UnitRange{Int64}, 6) with element type SubArray{Int64,1,UnitRange{Int64},Tuple{UnitRange{Int64}},true}:
 [1, 2, 3, 4, 5, 6]
 [7, 8, 9, 10, 11, 12]
 [13, 14, 15, 16, 17, 18]
```

`data` 自体の値はコピーされません。代わりに、`getindex` が呼び出されるときに関数 [`datasubset`](@ref) が呼び出されます。特定のウィンドウのデータのコピーを実際に取得するには、関数 [`getobs`](@ref) を使用します。

```julia-repl
julia> A[1]
6-element SubArray{Int64,1,UnitRange{Int64},Tuple{UnitRange{Int64}},true}:
 1
 ⋮
 6

julia> getobs(A, 1)
6-element Array{Int64,1}:
 1
 ⋮
 6
```

オプションのパラメータ `stride` を使用して、各隣接ウィンドウの開始要素間の距離を指定できます。デフォルトでは、ストライドはウィンドウサイズと等しくなります。

```julia-repl
julia> slidingwindow(1:20, 6, stride = 3)
5-element slidingwindow(::UnitRange{Int64}, 6, stride = 3) with element type SubArray{Int64,1,UnitRange{Int64},Tuple{UnitRange{Int64}},true}:
 [1, 2, 3, 4, 5, 6]
 [4, 5, 6, 7, 8, 9]
 [7, 8, 9, 10, 11, 12]
 [10, 11, 12, 13, 14, 15]
 [13, 14, 15, 16, 17, 18]
```

オプションの（キーワード）パラメータ `obsdim` を使用すると、観測を示す次元を指定できます。詳細については `LearnBase.ObsDim` を参照してください。
