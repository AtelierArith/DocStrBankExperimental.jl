```
@uviews A B ... expr
```

配列 `A`, `B`, ... を `uview(`A`), uview(`B`), ...` に置き換え、`expr` の実行中に元の配列をガーベジコレクションから保護します。

これは次のように同等です。

```
GC.@preserve A B ... begin
    let A = uview(A), B = uview(B), ...
        expr
    end
end
```

unsafe view は `expr` のスコープを逃れることを許可してはいけません。元の配列は `expr` の実行中にサイズ変更/追加/etc.されてはいけません。
