```
siteinds(M::MPS)
siteinds(::typeof(first), M::MPS)
```

MPSの各テンソルで見つかった最初のサイトインデックスのベクトルを取得します。

```
siteinds(::typeof(only), M::MPS)
```

MPSの各テンソルで見つかった唯一のサイトインデックスのベクトルを取得します。1つ以上見つかった場合はエラーになります。

```
siteinds(::typeof(all), M::MPS)
```

MPSの各テンソルで見つかったすべてのサイトインデックスのベクトルを取得します。IndexSetsのベクトルを返します。
