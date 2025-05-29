```
RingInfo
```

ピクセルのリングに関する情報、すなわち、同じコラテチュードを持つHealpixマップ上のピクセルの集合。この型は「mutable」であるため、1つのオブジェクトを再利用することができ、さらなるメモリ割り当てなしで何度も使用できます。

この構造体で定義されているフィールドのリストは以下の通りです：

  * `ring`: 整数インデックス、範囲は
  * `firstPixIdx`: このリングに属する最初のピクセル（`RING`スキームを使用）のインデックス
  * `numOfPixels`: リング内の連続したピクセルの数
  * `colatitude_rad`: このリングのコラテチュードの値（ラジアン単位）
  * `shifted`: ブールフラグ; リング内の最初のピクセルの経度がゼロでない場合は`true`です。

# 参照

[`getringinfo!`](@ref)および[`getringinfo`](@ref)も参照してください。

# 例

```julia
import Healpix
res = Healpix.Resolution(256)

# リング#10に関する情報を表示
print(getringinfo(res, 10))
```
