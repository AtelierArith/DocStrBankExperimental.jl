```
viz!(object; kwargs...)
```

この関数は、プロットのために `UlamMethod` オブジェクト用の `Meshes.viz!` をラップします。

### メソッド

```
viz!(boundary; kwargs...)
```

境界をプロットします。

```
viz!(bins; kwargs...)
```

ビンをプロットします。

```
viz!(binner; kwargs...)
```

`binner.bins` をプロットします。

```
viz!(data; kwargs...)
```

ポイントの `2 x N` 行列をプロットします。

---

### `Meshes.viz!` のドキュメント文字列は以下に提供されています。

---

```
viz!(object; [options])
```

`options` を [`viz`](@ref) に転送して、既存のシーンで Meshes.jl `object` を視覚化します。 ```
