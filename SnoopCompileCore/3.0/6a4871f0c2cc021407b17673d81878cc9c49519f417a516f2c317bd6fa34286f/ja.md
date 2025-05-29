```
invs = @snoop_invalidations expr
```

`expr`を評価することによってトリガーされたメソッドキャッシュの無効化をキャプチャします。`invs`は、無効化された`Core.MethodInstance`のシーケンスと、整数（深さをエンコード）および文字列（無効化のソースを文書化）からなる「説明」を含んでいます。

低レベルで作業していない限り、基本的に`invs`を直接[`SnoopCompile.invalidation_trees`](@ref)に渡すことを常に望むでしょう。

# 拡張ヘルプ

`invs`は、「理由」がアイテムの後に来る形式です。メソッド削除は次のシーケンスを生成します。

```
[ゼロまたはそれ以上の (mi, "invalidate_mt_cache") ペア..., ゼロまたはそれ以上の (depth1 tree, loctag) ペア..., メソッド, loctag] ただし loctag = "jl_method_table_disable"
```

ここで`mi`は`MethodInstance`を意味します。`depth1`は`depth=1`から始まるシーケンスを意味します。

メソッド挿入は次のシーケンスを生成します。

```
[ゼロまたはそれ以上の (depth0 tree, sig) ペア..., delete_methodと同じ情報ですが、loctag = "jl_method_table_insert"]
```

権威あるリファレンスはJuliaの`src/gf.c`ファイルです。
