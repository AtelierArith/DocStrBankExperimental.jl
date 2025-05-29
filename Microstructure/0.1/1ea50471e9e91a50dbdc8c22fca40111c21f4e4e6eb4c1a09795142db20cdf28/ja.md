```
spherical_mean(
    image_file::String, 
    save::Bool=true, 
    acq_files::String...
)
```

入力DWI画像`image_file`に対して方向平均を実行し、正規化された球面平均信号と関連する画像プロトコルを持つMRIオブジェクトを返します。`image_file`はDWI画像ファイルのフルパスです。`save`は、smtおよび正規化されたsmt画像ボリュームとプロトコルを保存するかどうかを示します。ファイルを保存する場合、niftiおよびテキストファイル（.btable）は入力データと同じパスに保存されます。最後に、可変数の`acq_files`は、`image_file`内の各DWIの取得パラメータを示すテキストファイルです。受け入れられるファイル拡張子は、b値、勾配方向、エコー時間、拡散勾配の分離および持続時間のための.bvals/.bvecs/.techo/.tdelta/.tsmalldelです。

従来のモデリングのための.bvals/.bvecsに加えて、サイズを推定するモデル（例：軸索直径、細胞体半径）には.tdelta/.tsmalldelファイルが必要です。.techoは、データが複数のエコー時間で収集され、結合拡散緩和モデリングを行いたい場合に必要です。.tdelta/.tsmalldel/.techoファイルの形式は、.bvalsファイルと似ており（DWIボリュームの数と等しい長さのベクトル）、.tdelta/.tsmalldel/.techoファイルの単位はmsです。
