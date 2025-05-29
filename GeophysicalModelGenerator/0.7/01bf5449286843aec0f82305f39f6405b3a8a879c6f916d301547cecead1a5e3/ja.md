```
X,Y,Z = xyz_grid(X_vec::Any, Y_vec::Any, Z_vec::Any)
```

`X,Y,Z` グリッドを作成します。これは `lonlatdepth_grid` と同様に機能しますが、より適した名前が付けられています。

# 例 1: 3D グリッドの作成

```julia-repl
julia> X,Y,Z =  xyz_grid(10:20,30:40,(-10:-1)km);
julia> size(X)
(11, 11, 10)
```

詳細な例については `lonlatdepth_grid` を参照してください。
