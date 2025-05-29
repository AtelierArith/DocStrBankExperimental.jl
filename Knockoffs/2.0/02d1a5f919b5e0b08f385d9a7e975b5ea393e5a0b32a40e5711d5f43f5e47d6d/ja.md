```
hmm_knockoff(plinkname; [datadir], [plink_outfile], [fastphase_outfile], [outdir], [verbose], args...)
```

バイナリPLINK形式のファイルからHMMノックオフを生成します。これは、まずfastPHASEを実行し、その後にSesia、Sabatti、Candesによる「隠れマルコフモデルノックオフを用いた遺伝子ハンティング」のアルゴリズム2を実行することで行われます。

# 入力

  * `plinkname`: `.bed/.bim/.fam`サフィックスなしのバイナリPLINKファイル名。

# オプション引数

  * `datadir`: PLINKおよびfastPHASEファイルへのフルパス（デフォルト = 現在のディレクトリ）
  * `plink_outfile`: 出力PLINK形式名
  * `fastphase_outfile`: fastPHASEのalpha、theta、rファイルからの出力ファイル名
  * `args...`: `fastPHASE.fastphase_estim_param()`で受け入れられる任意のパラメータ

# 出力

  * `plink_outfile.bed`: `n × p`ノックオフ遺伝子型
  * `plink_outfile.bim`: SNPマッピングファイル。ノックオフは".k"で終わるSNP名を持ちます
  * `plink_outfile.fam`: サンプルマッピングファイル、これは元の`plinkname.fam`ファイルのコピーです
  * `fastphase_outfile_rhat.txt`: fastPHASEからの平均rハットファイル
  * `fastphase_outfile_alphahat.txt`: fastPHASEからの平均alphaハットファイル
  * `fastphase_outfile_thetahat.txt`: fastPHASEからの平均thetaハットファイル

```
