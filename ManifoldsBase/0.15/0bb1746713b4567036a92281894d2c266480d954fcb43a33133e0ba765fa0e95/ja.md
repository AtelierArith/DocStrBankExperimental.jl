```
copyto!(M::AbstractManifold, q, p)
```

`p`から`q`に値をコピーします。ここで、両方とも[`AbstractManifold`](@ref) `M`上の点です。この関数はデフォルトで`copyto!(q, p)`を呼び出しますが、`M`からの情報にもアクセスできるレベルで関数をオーバーライドすることが有用な場合があります。
