```
Connectivity{X,P}
```

`Pxest`の接続性で、`Pxest`の四分木または八分木の根のメッシュ情報を保持します。パラメータ`X`は、根が四角形の場合は4（2D、すなわちp4est）、六角形の場合は8（3D、すなわちp8est）です。

# フィールド

  * `pointer`: 型`P`のポインタは、`P4estTypes.P4est.p4est_connectivity`または`P4estTypes.P4est.p8est_connectivity`のいずれかを指すポインタである可能性があります。これらの型に関する詳細は、ヘルプドキュメントを参照してください。

# 使用法

```
Connectivity{4}(name::Symbol)
```

p4estの組み込みメッシュ接続性を使用して、四分木の森の根のための接続性メッシュを構築します。`name`の有効な値は次のとおりです。

  * `:unitsquare`: 単位正方形。
  * `:periodic`: 全周期単位正方形。
  * `:rotwrap`: 周期的単位正方形（左と右の面が同一視され、上下の面も同様）。
  * `:corner`: 角の周りの三木メッシュ。
  * `:pillow`: 二つの木が重なり合っている。
  * `:moebius`: 五つの木のメビウスバンド。
  * `:star`: 六つの木の星。
  * `:cubed`: 単位立方体の六つの面。
  * `:disk_nonperiodic`: 五つの木の平坦な球面ディスク。
  * `:icosahedron`: 球を正二十面体を使用してマッピングするため（詳細は`@doc P4estTypes.P4est.p4est_connectivity_new_icosahedron`を参照）。
  * `:shell2d`: 2D球面シェル。
  * `:disk2d`: 2Dディスクをマッピングします。

---

```
Connectivity{4}(:disk, periodic_x::Bool, periodic_y::Bool)
```

五つの木の平坦な球面ディスクのための接続性構造を作成します。引数`periodic_x`と`periodic_y`は、それぞれディスクがx方向およびy方向で周期的かどうかを決定します。

詳細情報については`@doc P4estTypes.P4est.p4est_connectivity_new_disk`を参照してください。

---

```
Connectivity{8}(name::Symbol)
```

p8estの組み込みメッシュ接続性を使用して、八分木の森の根のための接続性メッシュを構築します。`name`の有効な値は次のとおりです。

  * `:unitcube`: 単位立方体。
  * `:periodic`: 全周期単位立方体。
  * `:rotcubes`: いくつかの立方体を含む（これらは互いに回転してトポロジーのルーチンを強調します）。
  * `:rotwrap`: 主に周期的な単位立方体（詳細は`@doc P4estTypes.P4est.p8est_connectivity_new_rotwrap`を参照）。
  * `:shell`: 球面シェル（詳細は`@doc P4estTypes.P4est.p8est_connectivity_new_shell`を参照）。
  * `:sphere`: 固体の球（詳細は`@doc P4estTypes.P4est.p8est_connectivity_new_sphere`を参照）。
  * `:twocubes`: 二つの立方体。
  * `:twowrap`: 二つの立方体で、両端が周期的に同一視される。

---

```
Connectivity{8}(:torus, nsegments)
```

回転トーラスを構築する接続性構造を作成します。ここで`nsegments`は大円に沿った木の数です。

詳細情報については`@doc P4estTypes.P4est.p8est_connectivity_new_torus`を参照してください。

---

```
Connectivity{8}(:torus, nsegments)
```

回転トーラスを構築する接続性構造を作成します。ここで`nsegments`は大円に沿った木の数です。

詳細情報については`@doc P4estTypes.P4est.p8est_connectivity_new_torus`を参照してください。

---

```
Connectivity{X}(:twotrees, l_face, r_face, orientation) where {X}
```

ユーザー定義の方法で互いに回転する二つの木のための接続性構造を作成します（`X=4`は四分木、`X=8`は八分木）。ここで`l_face`と`r_face`はそれぞれ左と右の面の0ベースのインデックスです。引数`orientation`は、木が互いに対して持つ向きのコードを示します。

---

```
Connectivity{X}(vertices, elements) where {X}
```

与えられた頂点リストと要素から頂点への接続性を作成します。`X=4`は四角形用、`X=8`は六角形用です。

  * `vertices`: x、y、z座標に対応する列を持つ、頂点数×3の行列である必要があります（通常、2Dの森の場合、`z`座標はゼロになります）。
  * `elements`: 各要素を定義するために使用される頂点インデックスを持つ、頂点数×4または8の行列である必要があります。z順序を使用し、ゼロインデックスを使用する必要があります。

---

```
Connectivity{X}(filename::String) where {X}
```

`filename`でのABAQUS入力から接続性を作成します。`X=4`は四角形用、`X=8`は六角形用です。

例のABAQUS入力ファイルについては、`@doc P4estTypes.P4est.p4est_connectivity_read_inp`および`@doc P4estTypes.P4est.p8est_connectivity_read_inp`を参照してください。

# 参照

  * [`brick`](@ref): 長方形の[`Connectivity`](@ref)を作成するための関数。
  * [`connectivity`](@ref): [`Pxest`](@ref)の接続性を取得するための関数。
  * [`refine`](@ref): 洗練された[`Connectivity`](@ref)を作成するための関数。
