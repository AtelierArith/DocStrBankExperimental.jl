```
swizzle!(v, value, indices...)
```

`v`を`indices`で変更し、`v[i₁] = value[1], v[i₂] = value[2], ...`となるようにします。ここで、`indices = (i₁, i₂, ...)`です。そして`value`を返します。

`indices`に重複するインデックスがある場合、`v`は対応するインデックスで連続的に上書きされ、`setindex!`のセマンティクスに従って最後の値が保持されます。
