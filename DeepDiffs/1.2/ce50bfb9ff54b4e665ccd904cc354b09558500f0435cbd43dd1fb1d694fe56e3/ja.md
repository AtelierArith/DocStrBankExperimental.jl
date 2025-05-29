diff = deepdiff(obj1, obj2)

deepdiffは2つのオブジェクト間の構造的な違いを計算し、obj1をobj2に変換するために必要な「編集」を表すdiffを返します。このdiffは、辞書のキーや配列のインデックスの`Set`を返す`added`、`removed`、および`modified`関数をサポートしています。
