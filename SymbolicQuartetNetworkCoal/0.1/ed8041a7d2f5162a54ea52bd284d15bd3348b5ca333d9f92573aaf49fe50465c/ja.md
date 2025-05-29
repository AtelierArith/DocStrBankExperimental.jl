```
makeEdgeLabel(net; showTerminalEdgeLabels=false)
```

エッジ番号をそのシンボリックラベルにマッピングするデータフレームを生成します。

## 説明

この関数は、`HybridNetwork`のエッジに対して、`"t_{e}"`という形式のラベルを作成します。ここで、`e`はエッジ番号です。デフォルトでは、ラベルは**非端末エッジ**（すなわち、葉ノードで終わらないエッジ）にのみ割り当てられます。出力データフレームは、PhyloPlotsのオプション`edgelabel=``の入力として使用されます。`showTerminalEdgeLabels=true`を設定すると、端末エッジのラベルも含まれます。

## 引数

  * `net`: `HybridNetwork`オブジェクト。
  * `showTerminalEdgeLabels`: ブールフラグ（デフォルト = `false`）。  

      * `false`: 端末エッジを除外します。
      * `true`: すべてのエッジを含めます。

## 戻り値

  * 列を持つ`DataFrame`:

      * `number`: エッジ番号。
      * `label`: 対応するシンボリックラベル（`"t_{e}"`）。
