```
eigenmodes(m::LinearLayeredModel, freq=1.0; kwargs...) -> modes
```

モデル `m` の固有モードを計算します。`m` は `SeisModels` の `LinearLayeredModel` でなければなりません。

固有モードは、キーが放射状の順序 $n$、モードタイプ（球状モードは `:S`、トロイダルモードは `:T`、内核トロイダルモードは `:C`）および角度の順序 ℓ のタプルである `OrderedDict` として返されます。値は [`Mineos.Mode`](@ref) です。どのフィールドにどの情報が含まれているかの詳細については、[`Mineos.Mode`](@ref) を参照してください。

例えば、₀S₂を取得するには `modes[(0,:S,2)]` を実行し、₃T₈の場合は `modes[(3,:T,8)]` と書きます。構文 `modes[3,:T,8]` も許可されています。

### キーワード引数

#### モード選択

  * `radial=true`: 放射状モードを計算する（またはしない）。この場合、`nmin` と `nmax` は無視されます。
  * `spheroidal=true`: 球状モードを計算する（またはしない）。
  * `toroidal=true`: トロイダルモードを計算する（またはしない）。
  * `ic_toroidal=true`: 内核トロイダルモードを計算する（またはしない）。

#### 計算パラメータ

  * `eps=1e-10`: 積分スキームの精度。固有周波数は約 `2eps` から `3eps` の相対精度で正確です。周波数が100 mHz未満（周期が10秒以上）の場合、`eps` は `1e-7` に設定できます。100 mHzから200 mHz（周期が5秒から10秒）の周波数の場合、`eps` は `1e-12` と `1e-10` の間であるべきです。
  * `wgrav=10`: 重力項が無視されるmHzの周波数。
  * `lmin=1`, `lmax=20`: モードの最小および最大角度の順序。
  * `wmin=0.0`, `wmax=166.0`: 考慮すべきモード固有周波数の最小および最大値。
  * `nmin=0`, `nmax=10`: 計算する最小および最大分散ブランチ番号。

```
