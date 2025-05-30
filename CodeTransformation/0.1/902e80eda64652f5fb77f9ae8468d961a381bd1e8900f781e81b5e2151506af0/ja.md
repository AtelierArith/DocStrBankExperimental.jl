```
codetransform!(tr, dst, src)
```

関数 `src` のメソッドにコード変換関数 `tr` を適用し、変換されたメソッドを別の関数 `dst` に追加します。

例: 関数内の定数を検索して置き換えます。

```
g(x) = x + 13
function e end
codetransform!(g => e) do ci
    for ex in ci.code
        if ex isa Expr
            map!(x -> x === 13 ? 7 : x, ex.args, ex.args)
        end
    end
    ci
end
e(1) # 8 を返します
```
