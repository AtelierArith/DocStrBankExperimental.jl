```
genepop(infile::String; kwargs...)
```

Genepop形式のファイルをメモリに読み込み、PopDataオブジェクトとして扱います。

  * `infile::String` : Genepopファイルへのパス

### キーワード引数

  * `digits::Integer`: 各アレルを示す桁数（デフォルト: `3`）
  * `popsep::String` : `infile`内の集団を区切る単語（デフォルト: "POP"）
  * `silent::Bool`   : インポート中にファイル情報を表示するかどうか（デフォルト: `false`）
  * `allow_monomorphic::Bool` : データセットに単型遺伝子座を保持するかどうか（デフォルト: `false`）

### ファイルは標準のGenepopフォーマットに従う必要があります：

  * 最初の行はコメント（スキップされます）
  * 遺伝子座は最初の行の後に1行ごとにリストされ、カンマなしまたは単一のカンマ区切りの行で表示されます
  * 特定のキーワード（デフォルトは`POP`）を含む行が集団を区切る必要があります
  * サンプル名の直後に*カンマ*が続きます
  * ファイルは*タブまたはスペースで区切られています*（ただし両方は不可！）

### Genepopファイルの例：

```
wasp_hive.gen: ニューヨークのハチの集団
Locus1
Locus2
Locus3
pop
Oneida_01,  250230  564568  110100
Oneida_02,  252238  568558  100120
Oneida_03,  254230  564558  090100
pop
Newcomb_01, 254230  564558  080100
Newcomb_02, 000230  564558  090080
Newcomb_03, 254230  000000  090100
Newcomb_04, 254230  564000  090120
```

## 例

```
waspsNY = genepop("wasp_hive.gen", digits = 3, popsep = "pop")
```
