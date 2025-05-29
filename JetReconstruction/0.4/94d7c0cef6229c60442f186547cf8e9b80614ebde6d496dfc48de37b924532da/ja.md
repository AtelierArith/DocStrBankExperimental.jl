```
loadjets(filename; splitby=isspace, constructor=(px,py,pz,E)->LorentzVectorHEP(E,px,py,pz), VT=LorentzVector)
```

ファイルからジェットを読み込みます。

# 引数

  * `filename`: ジェットを読み込むファイルの名前。
  * `splitby`: ファイル内のデータを分割するために使用される区切り文字。デフォルトは `isspace`。
  * `constructor`: ジェットデータから `VT` オブジェクトを構築する関数。デフォルトは `(px,py,pz,E)->LorentzVector(E,px,py,pz)`。
  * `VT`: ジェットデータを格納するために使用されるベクトルの型。デフォルトは `LorentzVector`。

# 戻り値

  * 読み込まれたジェットを表す `VT` オブジェクトのベクトル。
