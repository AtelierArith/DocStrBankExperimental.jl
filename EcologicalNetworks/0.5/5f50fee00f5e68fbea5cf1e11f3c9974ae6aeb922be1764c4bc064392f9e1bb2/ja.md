この抽象型は、情報の種類に関係なくすべての単一部ネットワークをグループ化します。単一部ネットワークには、`S`と呼ばれる種のための*単一*のフィールドがあり、これは行列のサイズと同じ数の要素を持ちます。

任意の単一部ネットワークは、`UnipartiteNetwork(A, S)`（ここで`A`は相互作用の行列で、`S`は種名のベクトルであると仮定します）を使用して宣言することができます。または、`UnipartiteNetwork(A)`を使用することもでき、その場合は種が自動的に名前付けされます。
