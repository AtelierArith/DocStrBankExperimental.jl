```
readmultinewicklevel1(file)
```

拡張ニューイック形式の木/ネットワークのリストを含むテキストファイルを読み込み（1行に1つの木）、それらを[`readnewicklevel1`](@ref)のように変換します。具体的には、各木/ネットワークにおいて

  * 根は抑制され（もし次数が2であれば次数3になる）
  * 任意の多分岐は恣意的に解決され
  * 任意の欠損枝長は1に設定され
  * 10を超える枝長は10に設定され（これは共alescent単位での枝長を仮定します）
  * 任意の欠損γは(0.1, 0.9)に設定され

その他の詳細については[`readnewicklevel1`](@ref)を参照してください。

複数の木またはネットワークを変更せずに読み込むには、[`PhyloNetworks.readmultinewick`](@extref)を参照してください。

出力: HybridNetworkオブジェクトの配列。

"("で始まる各行は1つのトポロジーを記述していると見なされます。ファイルには無視される余分な行が含まれている場合があります。
