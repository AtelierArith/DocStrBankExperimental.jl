`OIDataSet`オブジェクトは、OI-FITSファイルの内容を格納します。測定を含むすべてのデータブロック（`OI_VIS`、`OI_VIS2`、`OI_T3`、`OI_FLUX`、および`OI_INSPOL`）はベクターに格納され、整数によってインデックス付けされます。名前付きデータブロック（`OI_ARRAY`、`OI_WAVELENGTH`、および`OI_CORR`）は、その名前（大文字に変換され、前後の空白が削除され、複数の空白が1つの通常の空白に置き換えられたもの）によってインデックス付けされます。

OI-FITSファイルを読み込むのは、次のいずれかの方法で簡単に行えます：

```
data = OIDataSet(filename)
data = read(OIDataSet, filename)
```

ここで、`filename`はファイルの名前です。キーワード`hack_revn`を使用すると、すべてのOI-FITSデータブロックのリビジョン番号（FITSキーワード`OI-REVN`）を強制することができます。`hack_revn`は整数に設定することができ、すべてのデータブロックに対して仮定するリビジョン番号、または現在のデータブロックのタイプと実際のリビジョン番号の2つの引数を取る関数に設定することができ、その関数は仮定するリビジョン番号を返します。たとえば、すべての`OI_VIS`データブロックに対してリビジョン番号1を強制し、他は変更しない場合：

```
data = OIDataSet(filename; hack_revn = (T, revn) -> (T === OI_VIS ? 1 : revn))
```

データセット内の`OI_VIS`データブロックをループ処理するには、次のようにします：

```
for db in data.vis
    ...
end
```

同様に、`vis2`、`t3`、`flux`、および`inspol`フィールドに対しても、`OI_VIS2`、`OI_T3`、`OI_FLUX`、および`OI_INSPOL`データブロックにアクセスできます。

データセットには、他にもいくつかの公開プロパティがあります：

```
data.target           # OI_TARGETデータブロック
data.instr[insname]   # `insname`という名前のOI_WAVELENGTHデータブロック
data.array[arrname]   # `arrname`という名前のOI_ARRAYデータブロック
data.correl[corrname] # `corrname`という名前のOI_CORRデータブロック
```
