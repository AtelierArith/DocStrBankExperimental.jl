```
SystemWithOutput{ST<:AbstractSystem, MT<:AbstractMap} <: AbstractSystem
```

出力を持つシステムのためのパラメトリック合成型です。システムの型（`ST`）とマップの型（`MT`）でパラメータ化されています。

### フィールド

  * `s`         – 型 `ST` のシステム
  * `outputmap` – 型 `MT` の出力マップ
