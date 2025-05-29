```
function UniformBZMesh(; br::Cell, origin, size, shift)
```

UniformBZMeshのカスタマイズされたコンストラクタ。パラメータのoriginとshiftは、メッシュをガンマ中心またはM-Pメッシュとしてカスタマイズするために提供されます。

# パラメータ:

  * `cell`: セル情報
  * `origin`: 原点のシフトを示す数値。実際の原点はorigin*(b1+b2+b3)になります。デフォルト値origin=-1/2は(0,0,0)を1st BZの中心に移動させ、origin=0はmesh[1,1,1]=(0,0,0)+shiftを作成します。
  * `size`: メッシュのサイズ
  * `shift`: メッシュポイントの追加kシフト。実際のシフトはshift*(b1/N1+b2/N2+b3/N3)になります。偶数Nの場合、shift=1/2は高対称点を避けつつ対称性を保持します。

```
