抽象配線図をJSONとしてシリアライズします。

JSONデータ形式は、ウェブプログラミングにおいて便利です。残念ながら、JSONグラフ形式の標準は広く採用されていません。私たちは、KEILERプロジェクトとその後継であるELK（Eclipse Layout Kernel）で使用されている形式と互換性のあるフォーマットを採用します。この形式は、ネストされたグラフやポートをサポートし、GraphMLと大まかに機能互換性があります。また、ノードの位置やサイズなどのレイアウト情報もサポートしています。

参考文献：

  * KEILERのJSONグラフ形式: https://rtsys.informatik.uni-kiel.de/confluence/display/KIELER/JSON+Graph+Format
  * ELKのJSONグラフ形式: https://www.eclipse.org/elk/documentation/tooldevelopers/graphdatastructure/jsonformat.html
