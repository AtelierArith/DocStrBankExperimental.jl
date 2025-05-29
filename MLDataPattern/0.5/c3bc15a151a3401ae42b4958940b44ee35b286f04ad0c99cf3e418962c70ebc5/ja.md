```
slidingwindow(f, data, size, [stride], [excludetarget], [obsdim]) -> LabeledSlidingWindow
```

`data`のベクトルのようなビューを返します。各要素は2つの要素からなるタプルです：

1. `size`の隣接する観測の固定サイズの「ウィンドウ」。デフォルトではこれらのウィンドウは重なりません。これは、`stride`を明示的に指定することで変更できます。
2. ウィンドウの単一のターゲット（またはターゲットのベクトル）。ターゲットの内容は、ラベルインデックス関数`f`によって定義されます。

ラベルインデックス関数`f`は、現在のウィンドウの最初の観測のインデックスを受け取り、そのウィンドウに関連するターゲットのインデックス（またはインデックスの集合）を返す単項関数です。

```julia-repl
julia> A = slidingwindow(i->i+6, 1:20, 6)
3-element slidingwindow(::##3#4, ::UnitRange{Int64}, 6) with element type Tuple{...}
 ([1, 2, 3, 4, 5, 6], 7)
 ([7, 8, 9, 10, 11, 12], 13)
 ([13, 14, 15, 16, 17, 18], 19)
```

出力には完全で境界内のウィンドウのみが含まれることに注意してください。これは、余分な観測が結果のビューから省略される可能性があることを意味します。

```julia-repl
julia> A = slidingwindow(i->i-1, 1:20, 6)
2-element slidingwindow(::##5#6, ::UnitRange{Int64}, 6) with element type Tuple{...}
 ([7, 8, 9, 10, 11, 12], 6)
 ([13, 14, 15, 16, 17, 18], 12)
```

上記のように、`f`がインデックスのベクトルを返すことも許可されています。これは、スキップグラムのような技術を模倣するのに役立ちます。

```julia-repl
julia> data = split("The quick brown fox jumps over the lazy dog")
9-element Array{SubString{String},1}:
 "The"
 "quick"
 ⋮
 "lazy"
 "dog"

julia> A = slidingwindow(i->[i-2:i-1; i+1:i+2], data, 1)
5-element slidingwindow(::##11#12, ::Array{SubString{String},1}, 1) with element type Tuple{...}:
 (["brown"], ["The", "quick", "fox", "jumps"])
 (["fox"], ["quick", "brown", "jumps", "over"])
 (["jumps"], ["brown", "fox", "over", "the"])
 (["over"], ["fox", "jumps", "the", "lazy"])
 (["the"], ["jumps", "over", "lazy", "dog"])
```

ターゲットが特徴と重なる場合、影響を受ける観測は両方に存在します。この動作を変更するには、オプションのパラメータ`excludetarget = true`を設定できます。これにより、ターゲットが特徴ウィンドウから削除されます。

```julia-repl
julia> slidingwindow(i->i+2, data, 5, stride = 1, excludetarget = true)
5-element slidingwindow(::##17#18, ::Array{SubString{String},1}, 5, stride = 1) with element type Tuple{...}:
 (["The", "quick", "fox", "jumps"], "brown")
 (["quick", "brown", "jumps", "over"], "fox")
 (["brown", "fox", "over", "the"], "jumps")
 (["fox", "jumps", "the", "lazy"], "over")
 (["jumps", "over", "lazy", "dog"], "the")
```

オプションの（キーワード）パラメータ`obsdim`を使用すると、どの次元が観測を示すかを指定できます。詳細については`LearnBase.ObsDim`を参照してください。
