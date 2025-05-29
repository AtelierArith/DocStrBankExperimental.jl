# ODEInterface

このJuliaモジュールは、初期値問題を解くためのFortranで書かれた常微分方程式（ODE）ソルバーへのインターフェースを提供します。問題の形式は次の通りです。

```
x' = rhs(t,x),      x(t₀) = x₀
```

または（「質量行列」Mをサポートするソルバーの場合）

```
M⋅x' = rhs(t,x),    x(t₀) = x₀.
```

## 「インターフェース」とは何を意味するのか？

このJuliaモジュールは、初期値問題を解くためのコードを含んでいませんが、コンパイルされたFortranソルバーと対話するためのコードを含んでいます。これが、このモジュールがODESuiteと呼ばれていない理由です。

## 現在サポートされているソルバーは？

現在、Prof. E. HairerおよびProf. G. Wannerによって書かれた以下のFortranソルバーがサポートされています：

  * dopri5: Dormand & Princeによる5(4)次の明示的ルンゲクッタ法
  * dop853: Dormand & Princeによる8(5,3)次の明示的ルンゲクッタ法
  * odex: 明示的中点法に基づくGBS外挿アルゴリズム
  * radau5: 5次の暗黙的ルンゲクッタ法（Radau IIA）
  * radau: 5から13の間の可変次数の暗黙的ルンゲクッタ法（Radau IIA）
  * seulex: 線形暗黙的オイラー法に基づく外挿アルゴリズム
  * rodas: 4(3)次のロゼンブロック法（おそらく特異な質量行列を持つ）

詳細は[Prof. Hairerのソフトウェアページ](http://www.unige.ch/~hairer/software.html)を参照してください。

さらに、[SLATEC共通数学ライブラリ](http://www.netlib.org/slatec/)から以下のFortranソルバーもサポートされています：

  * ddeabm: アダムス-バシュフォース-モールトン予測子-修正子法（次数1から12の間）
  * ddebdf: 後方差分法（次数1から5の間）

このODEInterfaceによってサポートされるソルバーの機能は次の通りです：

  * ソルバーへの出力関数の提供（例：密な出力やイベント位置のため）
  * ソルバーへの質量行列およびヤコビ行列の提供（バンド行列のサポートあり）
  * ソルバーの微調整のためのすべてのパラメータ
  * 「特別な構造」を持つ問題のサポート、詳細は`help_specialstructure`を参照

また、以下もサポートされています：

  * bvpsol: 非常に非線形な2点境界値問題のための境界値問題ソルバー。ローカル線形ソルバーまたはグローバルスパース線形ソルバーを使用します。**注意：`bvpsol`のライセンスは非商業利用のみをカバーしています。詳細は[ライセンス](./LICENSE.md)を参照してください。** P. Deuflhard、G. Bader、L. Weimannによって書かれ、[ZIBのCodeLib](http://elib.zib.de/pub/elib/codelib/en/bvpode.html)を参照。
  * colnew: コレクションを使用した混合次数システムのための多点境界値問題ソルバー。U. Ascher、G. Baderによって書かれ、[Colnewホームページ](https://people.sc.fsu.edu/~jburkardt/f77_src/colnew/colnew.html)を参照。
  * BVP*M-2: 欠陥とグローバルエラー制御を持つ境界値常微分方程式の数値解法のための境界値問題ソルバー。J. J. Boisvert、P.H. Muir、R. J. Spiteriによって書かれ、[BVP*M-2ページ](http://cs.stmarys.ca/~muir/BVP*SOLVER*Webpage.shtml)を参照。

## このモジュールの要件は？

このモジュールを使用するには、サポートされているFortranソルバーを*コンパイル*し、各ソルバーのための共有ライブラリを提供する必要があります。このモジュールのビルドスクリプトは、すべてのソルバーを自動的にコンパイルしようとします。しかし、異なるコンパイルオプションやコンパイラを使用して自分でコンパイルしたバージョンを使用することもできます。ソルバーのコンパイル方法や共有ライブラリの作成方法についての詳細情報（ヘルプトピック）については、`ODEInterface.help_solversupport`を呼び出してください。

## さらなるヘルプ

いくつかのヘルプトピックの概要については、`ODEInterface.help_overview`を参照してください。

## このモジュールの著者への連絡

このJuliaモジュールの著者は

```
 Dr. Christian Ludwig
 email: ludwig@ma.tum.de
   (テクニカル大学ミュンヘン 数学部)
```
