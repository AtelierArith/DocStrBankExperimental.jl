`Go(P::Presentation[,silent])`

`Go` は、プレゼンテーション `P` に対してティエッツ変換を実行します。これは、インタラクティブなティエッツ変換コマンドの中で最も便利なものかもしれません。一般的に、明示的に関与する低レベルのコマンドを呼び出すことからあなたを救うようなデフォルト戦略を提供します。

大まかに言えば、`Go` は、2つのフェーズを含む手続きのループで構成されています。*検索フェーズ*では、以下に説明する `Search` と `SearchEqual` を呼び出し、共通の部分語を置き換えることによって関係式の長さを短縮しようとします。*排除フェーズ*では、以下に説明する `Eliminate` コマンド（または、いくつかの管理オーバーヘッドを節約するために `Eliminate` のサブルーチン）を呼び出し、残りの生成子の単語として表現できる生成子を排除しようとします。

`Go` が生成子の数、関係式の数、またはすべての関係式の合計長を減少させることに成功した場合、印刷レベルをゼロに設定していない限り、新しい状態を表示してから戻ります。ただし、これら3つの値がすべて変更されていない場合、たとえ `SearchEqual` コマンドがプレゼンテーションを変更して次の `Go` 呼び出しがさらなる進展をもたらす可能性があっても、出力は提供されません。したがって、そのような場合には、コマンドの呼び出しを何度も繰り返す（または、次に説明する `GoGo` コマンドを呼び出す）ことが理にかなっています。

例として、`PSL(2,17)` のインデックス 408 の部分群のプレゼンテーションを計算します。

|    gap> F2 := FreeGroup( "a", "b" );;     gap> G := F2 / [ F2.1^9, F2.2^2, (F2.1*F2.2)^4, (F2.1^2*F2.2)^3 ];;     gap> a := G.1;;  b := G.2;;     gap> H := Subgroup( G, [ (a*b)^2, (a^-1*b)^2 ] );;     gap> Index( G, H );     408     gap> P := PresentationSubgroup( G, H );     << 生成子が 8 つ、関係式が 36 で合計長が 111 のプレゼンテーション >>     gap> DisplayPresentation(P);     1: a=A     2: g=G     3: c=C     4: f=F     5: h=H     6: d=D     7: fbc=1     8: dBa=1     9: gdb=1     10: ceb=1     11: eab=1     12: caB=1     13: BBB=1     14: cBd=1     15: acb=1     16: afB=1     17: bbb=1     18: bac=1     19: cba=1     20: aBc=1     21: haB=1     22: dab=1     23: Bec=1     24: Bad=1     25: Bca=1     26: bbb=1     27: afB=1     28: agb=1     29: agb=1     30: ab=BA     31: ab=bC     32: ab=BA     33: ac=Ce     34: ac=bb     35: cB=bC     36: aca=CAC     gap> P.primaryGeneratorWords;     [ b, a*b*a ]     gap> P.protected := 2;;     gap> P.debug := 2;;     gap> simplify( P );     &I  eliminating *x7 = _x5     &I  eliminating _x5 = _x4     &I  eliminating _x18 = _x3     &I  eliminating _x8 = _x3     &I  there are 4 generators and 8 relators of total length 21     &I  there are 4 generators and 7 relators of total length 18     &I  eliminating _x4 = _x3^-1**x2^-1     &I  eliminating *x3 = _x2**x1^-1     &I  there are 2 generators and 4 relators of total length 14     &I  there are 2 generators and 4 relators of total length 13     &I  there are 2 generators and 3 relators of total length 9     gap> relators( P );     &I  1. *x1^2     &I  2. _x2^3     &I  3. _x2**x1**x2**x1 |

2つのフェーズのループの回数や、各フェーズでの部分語検索や生成子排除の回数は、結果のプレゼンテーションや計算時間に大きく影響を与える可能性のあるオプションパラメータのセットによって決まります（以下のティエッツオプションを参照）。

`Go` は、`simplify` コマンドの別名に過ぎません。この名前は、ANU ティエッツ変換スタンドアロンプログラムの *go* オプションや SPAS の *go* コマンドからその名前に慣れている {GAP} ユーザーの便宜のために導入されました。

"silent" が true として指定されている場合、T.debug=1 の場合に `Go` によるステータスラインの印刷は抑制されます。
