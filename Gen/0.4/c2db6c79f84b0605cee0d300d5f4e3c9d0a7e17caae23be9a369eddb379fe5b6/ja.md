```
@pkern function k(trace, args...; 
                  check=false, observations=EmptyChoiceMap())
    ...
    return trace, metadata
end
```

ジュリア関数を原始的定常カーネルとして宣言します。

関数の最初の引数はトレースであり、関数の戻り値は `(trace, metadata)` であるべきです。ここで `metadata` はユーザーが提供するものであり、受け入れ拒否の決定の結果のような有用な情報である可能性があります。

キーワード引数 `check` と `observations` が必要です。
