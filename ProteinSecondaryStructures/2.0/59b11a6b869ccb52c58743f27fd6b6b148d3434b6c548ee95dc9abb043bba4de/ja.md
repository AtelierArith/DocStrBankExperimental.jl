```
stride_run(pdb_file::AbstractString; adjust_pdb=false)
```

PDBファイルに対してstrideを実行し、各残基の`stride`詳細二次構造情報を含むベクターを返します。

  * `adjust_pdb=true`は、`stride`を実行する前にPDBファイルのフォーマットを調整するために使用され、特定のヘッダーと特定の空のチェーン識別子が必要です。この場合、PDBファイルにはATOM行のみが保持されます。
  * `adjust_pdb=false`の場合、提供されたPDBファイルはそのまま使用されます。

残基または原子のタイプが認識されない場合や、PDBファイルのヘッダーが必要なパターンに従っていない場合、`STRIDE`は失敗します。

!!! note
      * STRIDEは、認識されないか不完全な場合、PDBファイル内のいくつかの残基を無視する可能性があります。
      * STRIDEはmmCIF形式の構造をサポートしていません。

