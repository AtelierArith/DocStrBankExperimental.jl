```
vcf(infile::String; ; rename_loci::Bool, silent::Bool, allow_monomorphic::Bool)
```

VCFファイルをメモリにPopDataオブジェクトとしてロードします。集団情報は別途提供する必要があります。

  * `infile` : VCFファイルへのパス（gzip圧縮可能）

**キーワード引数**

  * `rename_loci` : loci名を「snp_#」に簡略化するかどうかの真偽値（デフォルト: `false`）
  * `allow_monomorphic` : 単型lociを保持するかどうかの真偽値（デフォルト: `false`）
  * `silent`: 追加のファイル情報を印刷するかどうかの真偽値（デフォルト: `false`）。

アレルは以下のスキーマに従って再コーディングされます：

| **Base**   |  A  |  T  |  C  |  G  |
|:---------- |:---:|:---:|:---:|:---:|
| **Allele** |  1  |  2  |  3  |  4  |

### 混合倍数データ

混合倍数データ（例えばpoolseq）をインポートする場合、遺伝子型列を正しい`GenoArray`型に変換するために追加のステップを実行する必要があります：

## 例

```julia
julia> mydata = vcf("path/to/file.vcf", silent = true, rename_loci = true) ;

julia> mydata.genodata.genotype =  mydata.genodata.genotype |> Array{Union{Missing, NTuple}}
```
