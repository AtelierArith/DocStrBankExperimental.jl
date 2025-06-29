`XSP(ρ,s,n,even=false)`

は、`even=true` の場合はすべての `d` が偶数のとき、そうでない場合はすべての `d` が奇数のときに、[Lusztig-Spaltenstein 1985](biblio.htm#LuSp85) の $X̃^{ρ-s,s}_{n,d}$ の合併を返します。これらの記号は、古典群の非可換共役類に対する局所系をパラメータ化します。[Lusztig2004](biblio.htm#Lus04) の 13.2 では、記法は ${}^ρ X^s_{n,d}$ です。結果は、各類似クラスに対応するリストのリストであり（これはサポートに対する特定の共役類に対応します）、`s==0` の場合は正の欠陥のみが考慮されます。

  * `XSP(2,1,n)` は Sp₂ₙ の L-S 記号を返します
  * `XSP(4,2,n)` は char.2 の Sp₂ₙ の L-S 記号を返します
  * `XSP(2,0,n)` は SO₂ₙ₊₁ の L-S 記号を返します [欠陥は奇数]
  * `XSP(2,0,n,true)` は SO₂ₙ の L-S 記号を返します [欠陥は偶数]
  * `XSP(4,0,n,true)` は char 2 の SO₂ₙ の L-S 記号を返します

各項目は、局所系に関する情報を提供する `NamedTuple` です。フィールドは次のとおりです。

  * `symbol` は Lusztig-Spaltenstein 記号です
  * `dimBu` は局所系のサポート `u` の次元です
  * `Au` は局所系の `A(u)` のキャラクターをリストとして説明します：`true`->sgn, `false`->Id
  * `sp` は一般化されたスプリンガー対応のパラメータ（相対ウィール群のキャラクター）です
