mpglu!(MPGA::MPGArray; residterm=residtermdefault) MPGArrayを構造体からの割り当てを使用して因数分解します。

この関数は低精度コピーを因数分解し、高精度行列はそのままにします。MPGArrayのコンストラクタは、`basissize` KylovベクトルとGMRESが必要とするその他のいくつかのもののためにストレージを割り当てます。出力として因数分解オブジェクトが得られ、線形システムを解くために`\`を使用できます。

kwarg `residterm`は終了基準を設定します。`residterm == true`（デフォルト）は、小さな残差で反復を終了します。`residterm == false`は、小さなノルム逆誤差で反復を終了します。詳細についてはドキュメントを参照してください。
