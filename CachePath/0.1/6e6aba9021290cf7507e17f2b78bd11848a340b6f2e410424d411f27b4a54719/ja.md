```
@cpimport module depot_path::AbstractString
```

`module`を`depot_path`を使用してインポートし、プリコンパイルキャッシュを保存および取得します。別の場所に存在するプリコンパイルキャッシュは無視されます。

`@cpimport`の意味は、他の方法での`import`とは異なる可能性があります。

# 例:

プリコンパイルキャッシュの保存および取得のために"./newdepot"を使用して`Example`モジュールをインポートします。

```
julia> @cpimport Example "./newdepot"
```
