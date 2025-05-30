`@showlnt x` は "x = val" を出力します。ここで `val` は `x` の値であり、このステートメントが実行された関数、ファイル、および行番号に関する情報が表示され、再帰の深さを示すためにインデントが使用されます。例えば：

```julia
function recurses(n)
    @showlnt n
    n += 1
    @showlnt n
    if n < 10
        n = recurses(n)
    end
    return n
end
```

は次のような出力を生成するかもしれません：

```
        x = 5
        (in foo at ./error.jl:26 at /tmp/showln_test.jl:52)
        x = 7
        (in foo at ./error.jl:26 at /tmp/showln_test.jl:54)
```

このマクロはバックトレースを取得し、対応するコード情報を調べるのは比較的高コストであるため、`@showlnt` を使用するとかなりのパフォーマンスコストがかかる可能性があります。

行のインデントはバックトレースの長さに比例し、したがって再帰の深さの指標となります。
