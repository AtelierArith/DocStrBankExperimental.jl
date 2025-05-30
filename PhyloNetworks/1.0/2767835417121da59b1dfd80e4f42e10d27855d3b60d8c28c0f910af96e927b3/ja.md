```
readnexus_treeblock(filename, treereader=readnewick, args...;
                    reticulate=true, stringmodifier=[r"#(\d+)" => s"#H\1"])
```

nexus形式のファイルの*最初の* "trees" ブロックを読み取り、翻訳テーブルが存在する場合はそれを使用し、`HybridNetwork`のベクターを返します。`[&...]`内の情報はコメントとして解釈され、デフォルトのツリーレーダーによって破棄されます。オプションの引数`args`はツリーレーダーに渡されます。

nexus形式の詳細については、[Maddison, Swofford & Maddison (1997)](https://doi.org/10.1093/sysbio/46.4.590)を参照してください。

`reticulate`がfalseでない限り、リテキュレーションを持つネットワークを読み取るために以下の処理が行われます。

各系統樹を読み取る前に、各`#number`のインスタンスは、ハイブリッドノードで標準の拡張Newick形式に適合させるために`#Hnumber`に置き換えられます。この動作は、`stringmodifier`オプションで変更可能で、`replace`によって受け入れられるペアのベクターである必要があります。

継承γ値は、*マイナー*ハイブリッドエッジの"コメント"ブロック内に与えられていると仮定されます（拡張Newickを形成するためにチップとしてカットされる）例えば、bacterによって出力されたもののように、次のようになります ([Vaughan et al. 2017](http://dx.doi.org/10.1534/genetics.116.193425)):

```
#11[&conv=0, relSize=0.08, ...
```

または、SpeciesNetworkによって出力されたもののように、次のようになります ([Zhang et al. 2018](https://doi.org/10.1093/molbev/msx307)):

```
#H11[&gamma=0.08]
```

この例では、ハイブリッドH11に対応するエッジはγ=0.08です。
