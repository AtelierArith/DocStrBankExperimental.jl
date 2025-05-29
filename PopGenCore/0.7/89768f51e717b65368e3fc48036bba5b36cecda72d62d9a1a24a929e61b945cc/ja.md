```
plink(infile::String; keepfields::Symbol|Vector{Symbol}, silent::Bool)
```

PLINKの`.ped`またはバイナリの`.bed`ファイルをメモリに読み込み、`PopData`オブジェクトとして扱います。同じディレクトリに対応する`.fam`ファイルが必要ですが、対応する`.bim`ファイルはオプションです。

  * `infile::String` : `.ped`または`.bed`ファイルへのパス

### キーワード引数

  * `famfields::Symbol|Vector{Symbol}` : `.fam`ファイルからインポートする追加フィールド

      * `:all` [デフォルト]
      * `:none`
      * `[:sire, :dam, :sex, :phenotype]`のいずれかまたは組み合わせ
  * `bimfields::Symbol|Vector{Symbol}` : オプションの`.bim`ファイルからインポートする追加フィールド

      * `:all` [デフォルト]
      * `:none`
      * `[:chromosome, :cm, :bp]`のいずれかまたは組み合わせ
  * `silent::Bool`   : インポート中にファイル情報を表示するかどうか（デフォルト: `false`）

## 例

```julia
para = plink("datadir/parakeet.ped", famfields = :sex)
parr = plink("datadir/parrot.bed", famfields = [:sire, :dam], bimfields = :chromosome)
```
