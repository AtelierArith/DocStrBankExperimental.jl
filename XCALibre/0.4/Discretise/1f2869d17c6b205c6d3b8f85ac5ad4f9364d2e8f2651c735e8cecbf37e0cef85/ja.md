```
construct_periodic(mesh, backend, patch1::Symbol, patch2::Symbol)
```

周期境界条件を構築するための関数。

### 入力

  * `mesh` – メッシュ。
  * `backend`  – バックエンドの設定。
  * `patch1`  – 主な周期パッチID。
  * `patch2`   – 隣接する周期パッチID。

### 出力

  * periodic::Tuple - `patch1` と `patch2` の境界定義を含むタプル、すなわち (periodic1, periodic2)。`periodic1` と `periodic2` のフィールドは次の通りです。

      * `ID` – メッシュオブジェクト内の境界情報にアクセスするためのインデックス
      * `value` – 次のキーワード引数を持つ `NamedTuple` を表します：

          * index – メッシュオブジェクト内の境界幾何情報を見つけるために使用されるID
          * distance – パッチ間の垂直距離
          * face_map – 一致するパッチの面へのインデックスを提供するベクター
          * ismaster – パッチペアの1つを主パッチとして識別するフラグ

### 例

```
- `periodic = construct_periodic(mesh, CPU(), :top, :bottom)` - `top` と `bottom` という名前の周期境界を持つCPUバックエンドを使用した例。
```
