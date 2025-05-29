```
permissive(tns, dims...)
```

`PermissiveArray`を作成します。ここで、`permissive(tns, dims...)[i...]`は、`dims[n]`が`true`のときに`i[n]`が`tns`の範囲内にない場合は`missing`になります。このラッパーは、すべての許容次元が次元チェックから免除されることを可能にし、配列の範囲外にアクセスする必要がある場合やパディングに便利です。より正式には、

```
    permissive(tns, dims...)[i...] =
        if any(n -> dims[n] && !(i[n] in axes(tns)[n]))
            missing
        else
            tns[i...]
        end
```
