```
save(job::Job)
```

ジョブの計算と `job.sh` 提出スクリプトを `job.dir` に保存します。フラグ、実行ファイル、擬似ポテンシャルなどの有効性についていくつかのサニティチェックが行われます。また、ジョブは後で簡単に取得できるように登録されます。

ジョブディレクトリに以前のジョブが存在する場合（有効なジョブスクリプトによって示される）、それは `.versions` サブディレクトリに `job` の以前のバージョンとしてコピーされ、`job` のバージョンがインクリメントされます。
