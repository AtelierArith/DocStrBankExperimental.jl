# 拡張ヘルプ

```
isuniversal(L::Line; [witness::Bool]=false)
```

### アルゴリズム

  * `witness` が `false` の場合、結果は周囲の次元が1であれば `true` になり、

それ以外の場合は `false` になります。

  * `witness` が `true` の場合、結果は周囲の次元が1であれば `(true, [])` になり、

それ以外の場合は `(false, v)` で、$v ∉ P$ となります。
