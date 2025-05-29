```
uniquename(str, dlm="\$"; modify_first=false, counter=GLOBAL_NAME_COUNTER)
```

文字列入力 `str` が `n` 回目のとき、`str * dlm * string(n)` を返します。

もし `str` がすでに `str0 * dlm * n` の形式でフォーマットされている場合、ここでの `n` は整数であり、`str0` は `n` と `str0` がカウントされた回数に1を加えたものの大きい方が使用されます。

`modify_first` が `false` の場合、`uniquename(str, dlm; modify_first=false)` が呼ばれた最初のときに `str` が返されます。

これはプログラム的にセルを作成し、それらが最終的に GDSII ファイルに保存される場合に便利です。

一意性は、各 Julia セッションごとに期待されるか、または [`reset_uniquename!`](@ref) が呼ばれるまで持続しますので、既存の GDSII ファイルを読み込んで、その上にユニークなセルを保存しようとすると、不運な衝突が発生する可能性があります。すべての読み込まれた `Cell` 名に対して `uniquename` を呼び出すことで、実質的にそれらを「登録」し、以降の `uniquename` 呼び出しがそれらを認識できるようになります。

# 例

```jldoctest
julia> reset_uniquename!();

julia> uniquename("name"; modify_first=true)
"name\$1"

julia> uniquename("name\$4")
"name\$4"

julia> uniquename("name\$3")
"name\$5"

julia> uniquename("name")
"name\$6"
```

`counter` は、各名前がどれだけ見られたかをカウントする `Dict{String,Int}` です。デフォルトは、Julia セッションの終了までまたは [`reset_uniquename!`](@ref) が呼ばれるまで持続するグローバルカウンターです。
