The Chevieパッケージは、同名のGAP3パッケージのJuliaへのポートとして始まりました。このポートは2018年末に始まり、パッケージはまだ流動的であるため、一部の関数名やインターフェースはまだ変更される可能性があります。プルリクエストや問題の報告は歓迎します。

私はChevieを動作させるために必要なGAPの機能を実装しました。このインフラストラクチャのほとんどはすでに別のパッケージとして登録されています。これらのパッケージは、類似の機能を提供する他のJuliaパッケージと比較して利点があるかもしれませんので、ぜひご覧ください。これらのパッケージは読み込まれ、再エクスポートされるため、`Chevie`を使用するとその機能が自動的に利用可能になります。言い換えれば、`Chevie`は以下のパッケージのメタパッケージです：

  * (単変数) [LaurentPolynomials](https://github.com/jmichel7/LaurentPolynomials.jl)（および有理数）
  * (多変数) [PuiseuxPolynomials](https://github.com/jmichel7/PuiseuxPolynomials.jl)（および分数指数がない場合の有理数）
  * [CyclotomicNumbers](https://github.com/jmichel7/CyclotomicNumbers.jl)（巡回体の要素）
  * [ModuleElts](https://github.com/jmichel7/ModuleElts.jl)（ある環の自由モジュールの要素）
  * [Combinat](https://github.com/jmichel7/Combinat.jl)（組合せ論と基本的な数論）
  * [PermGroups](https://github.com/jmichel7/PermGroups.jl)（置換、群、置換群。モジュール`Perms`と`Groups`を含み、これらは別のパッケージになる可能性があります）
  * [SignedPerms](https://github.com/jmichel7/SignedPerms.jl)（符号付き置換）
  * [MatInt](https://github.com/jmichel7/MatInt.jl)（整数行列と格子）
  * [CycPols](https://github.com/jmichel7/CycPols.jl)（巡回多項式）
  * [GenLinearAlgebra](https://github.com/jmichel7/GenLinearAlgebra.jl)（任意の体/環上の線形代数）
  * [FinitePosets](https://github.com/jmichel7/FinitePosets.jl)（有限部分順序）
  * [FiniteFields](https://github.com/jmichel7/FiniteFields.jl)（有限体）
  * [GroupPresentations](https://github.com/jmichel7/GroupPresentations.jl)（群の表現、および生成子と関係によって定義された群）
  * [UsingMerge](https://github.com/jmichel7/UsingMerge.jl)（現在の環境でパッケージを自動的に構成）

上記のパッケージのドキュメントを参照して、それらの機能の使い方を確認してください。

私は現在`Chevie`に存在する他のインフラストラクチャも実装しましたが、最終的には別のパッケージになる可能性があります：

  * 有限体上の多項式の因数分解（モジュール`FFfac`）
  * 有理数上の多項式の因数分解（モジュール`Fact`）
  * 巡回体の部分体である数体（モジュール[`Nf`](@ref)）

置換群に関しては、GAPの高度なアルゴリズムをしばしば単純で書きやすい方法に置き換えましたが、これは小さな群にのみ適しています（パッケージの残りには十分ですが、あなたのニーズには合わないかもしれません）。それ以外の場合、インフラストラクチャコードはしばしばGAPと競争力があり、はるかに少ないコードを使用しています（しばしば100行のJuliaが1000行のCを置き換えます）；そして、私が行ったよりも最適化できると確信しています。コードと設計に関するコメントは歓迎します。効率が悪すぎるか、実装が難しいと感じた関数（任意の群のキャラクターテーブルなど）については、`Chevie`は`GAP`パッケージを拡張として使用します。これは、`GAP`パッケージがインストールされている場合、`Chevie`が自動的に`GAP`を呼び出してこれらの関数を実装することを意味します。

`Chevie.jl`パッケージの関数は、GAP3/Chevieの同等の関数よりもしばしば10倍速いです（最初の実行時の非常に長いコンパイル時間の後に –– JuliaのTTFP）。

`Chevie`パッケージは現在、GAP3 Chevieの機能のほぼすべてを実装しています（GAP3 AlgebraおよびVKcurveパッケージの一部の機能も含まれています）。また、GAP3 Chevieには存在しない新しい機能もいくつかあります。GAP3/Chevieのユーザーであれば、`gap`関数を使用して、GAP3の関数に対応する`Chevie.jl`の機能を見つけることができます：これは文字列を受け取り、その文字列に一致するGAP3の関数のJulia翻訳を返します（大文字と小文字は区別されません）。

```julia-rep1
julia> gap("words")
CharRepresentationWords  =>  traces_words_mats
CoxeterWords(W[,l])      =>  word.(Ref(W),elements(W[,l]))
GarsideWords             =>  elements
```

見つけた関数のオンラインヘルプにアクセスできます。

### インストール

これは登録されたパッケージで、標準的な方法でインストール/アップグレードできます。Juliaの初心者の方には、これが何であるかを思い出させておきます。インストールするには、REPLのコマンドラインで次のようにします：

  * パッケージモードに入るには]
  * コマンドを実行します

```
(@v1.10) pkg> add Chevie
```

  * パッケージモードを終了するにはバックスペースを押し、その後

```
julia> using Chevie
```

と入力すれば、セットアップ完了です。最初のヘルプを得るには、`?Chevie`と入力してください。

後で最新バージョンに更新するには、次のようにします。

```
(@v1.10) pkg> update
```

`Chevie.jl`はJulia 1.10以降が必要です。
