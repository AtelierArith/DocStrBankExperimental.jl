```
textwrap(s::T where T<:AbstractString, width::Real, pos::Point;
    rightgutter=5,
    leading=0)
textwrap(s::T where T<:AbstractString, width::Real, pos::Point, linefunc::Function;
    rightgutter=5,
    leading=0)
```

文字列 `s` を空白文字で分割して行に描画し、各行が `width` 単位を超えないようにします。テキストは `pos` から始まり、最初の行のテキストはその位置を水平に通過する線の下に完全に描画されます。各行は左側に揃えられ、`pos` の下に配置されます。

`textbox()` も参照してください。

オプションとして、各行の前に関数 `linefunc(linenumber, linetext, startpos, leading)` を実行します。

`leading` の値を指定しない場合、フォントの組み込みのエクステントが使用されます。

空白文字がないテキストは折り返されません。文字列や配列をチャンクに分割する簡単なチャンク関数を書くことができます：

```julia
chunk(x, n) = [x[i:min(i+n-1,length(x))] for i in 1:n:length(x)]
```

例えば：

```julia
textwrap(the_text, 300, boxtopleft(BoundingBox()) + 20,
    (ln, lt, sp, ht) -> begin
        c = count(t -> occursin(r"[[:punct:]]", t), split(lt, ""))
        @layer begin
            fontface("Menlo")
            sethue("darkred")
            text(string("[", c, "]"), sp + (310, 0))
        end
    end)
```

は、各行の最後に句読点の数をカウントして表示します。

次の行が描画される位置を返します。
