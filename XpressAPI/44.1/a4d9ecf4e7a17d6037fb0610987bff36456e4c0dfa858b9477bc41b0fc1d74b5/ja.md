```
XPRS_TREECOMPRESSION
```

ノードをグローバルファイルに書き込む際、最適化プログラムはデータ圧縮技術を使用してディスク上のツリーファイルのサイズを削減しようとすることがあります。（整数）

`TREECOMPRESSION`制御は、使用されるデータ圧縮アルゴリズムの強度を決定します。高い値はパフォーマンスを低下させる影響を受けながら優れたデータ圧縮を提供し、低い値はより迅速に圧縮しますが、効果はそれほど高くありません。`TREECOMPRESSION`が0に設定されている場合、ツリーファイルにはデータ圧縮が使用されません。

デフォルト値: `2`

ドメイン: 0,1,2,3,4,5,6,7,8,9
