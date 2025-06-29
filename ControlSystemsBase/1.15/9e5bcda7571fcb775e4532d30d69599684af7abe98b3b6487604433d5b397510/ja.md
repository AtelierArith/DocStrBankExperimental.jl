```
relative_gain_array(G, w::AbstractVector)
relative_gain_array(G, w::Number)
```

`G`の相対ゲイン配列を周波数`w`で計算します。 G(iω) .* pinv(tranpose(G(iω)))

RGAは、個別に調整されたループを使用してMIMO制御の入力-出力ペアリングを見つけるために使用できます。 クロスオーバー周波数でRGA(ωc)ができるだけ対角に近くなるように入力と出力をペアにします。 RGA(0)に負の対角要素が含まれるようなペアリングは避けてください。

  * RGAのエントリの絶対値の合計は、Gの「真の条件数」の良い指標であり、`G`の入力/出力スケーリングによって達成できる最良の条件数です。 -Glad, Ljung。
  * RGAは`G`の入力/出力スケーリングに対して不変です。
  * RGAに大きなエントリが含まれている場合、システムはモデル誤差に敏感である可能性があります。 -Skogestad, "Multivariable Feedback Control: Analysis and Design":

      * 入力チャネルの不確実性（対角入力不確実性）。 クロスオーバー周波数付近に大きなRGA要素を持つプラントは、入力の不確実性（例えば、不確実または無視されたアクチュエータダイナミクスによって引き起こされる）に対する感度のために根本的に制御が難しいです。 特に、デカップラーや他の逆ベースのコントローラーは、大きなRGA要素を持つプラントには使用すべきではありません。
      * 要素の不確実性。 大きなRGA要素は、要素ごとの不確実性に対する感度を示唆します。

    ただし、この種の不確実性は、伝達関数要素間の物理的結合のために実際には発生しない場合があります。 したがって、対角入力不確実性（常に存在する）は、大きなRGA要素を持つプラントにとって通常はより懸念されます。

相対ゲイン配列は、単位一貫性（UC）一般化逆行列を使用して計算されます。 参考文献: "On the Relative Gain Array (RGA) with Singular and Rectangular Matrices" Jeffrey Uhlmann https://arxiv.org/pdf/1805.10312.pdf ```
