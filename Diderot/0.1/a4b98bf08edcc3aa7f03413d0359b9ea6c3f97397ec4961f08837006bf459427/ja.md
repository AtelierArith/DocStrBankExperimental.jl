# Diderot.jl

Juliaにおける離散最適化のための決定図。

[![](https://img.shields.io/badge/docs-stable-blue.svg)](https://rschwarz.github.io/Diderot.jl/stable) [![](https://img.shields.io/badge/docs-dev-blue.svg)](https://rschwarz.github.io/Diderot.jl/dev) [![Build Status](https://travis-ci.com/rschwarz/Diderot.jl.svg?branch=master)](https://travis-ci.com/rschwarz/Diderot.jl) [![Codecov](https://codecov.io/gh/rschwarz/Diderot.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/rschwarz/Diderot.jl)

決定図（層状状態遷移グラフのトップダウン構築）の一般的な実装を提供します。図の正確なカットセットのノードによって定義されたサブ問題を持つ分枝限定法アルゴリズムを実装しています。

新しい問題クラスをサポートするためには、インスタンスのユーザー定義型に対してディスパッチされるいくつかのメソッドを実装する必要があります。これにより、状態と遷移関数を記述します。

ソルバーの動作（制約、緩和、変数の順序、図の幅）は、ユーザー定義のレイヤ処理を通じて完全にカスタマイズ可能です。

## 動機

このパッケージは主に学習実験として書かれています。アイデアを実装することで、単にそれについて読むよりも、課題に対する深い理解が得られます。

離散最適化における決定図の魅力は二重です：

1. アルゴリズムの単純さにより、ゼロからの実装が合理的な試みとなります。
2. DDベースの分枝限定法は並列化に適しているようで、MIPソルバーよりも良いスピードアップを得られるようです。

## 制限事項

これは（まだ）主に素朴な教科書の実装です。データ構造の選択や頻繁な割り当てを避ける点で改善の余地があると確信しています。

現在、目的関数は最大化されると仮定されており、遷移値は加算によって結合されます。つまり、遷移の値を弧の重みとして使用し、図の中で最長経路を探しています。原則として、最小化を選択したり、別の演算子（乗算、最大値）を使用することも可能ですが、これにはさらに多くの型パラメータ化が必要になります。

決定図はすべての遷移弧を保持せず、動的に最長経路を計算します。つまり、新しいレイヤが作成された後、各ノードは単一の入射弧のみを記憶します。この簡略化は最適解を見つける目的にはうまく機能しますが、実行可能な解の列挙や最適性分析などの他の使用ケースを排除します。

## 問題クラス

特定の問題クラスのモデルとメソッドも、このパッケージのサブモジュールとして実装されています。主な動機は、現在のAPIをテストドライブし、十分に一般的であり、あまり冗長でないことを確認することです。

現在含まれているのは：

  * バイナリナップサック問題。
  * セットカバー問題。

## 参考文献

実装は、D Bergman、A Cire、WJ van Hoeve、J Hookerによる書籍[Decision Diagrams for Optimization](https://www.springer.com/us/book/9783319428475)に基づいています。

[MDDウェブサイト](http://www.andrew.cmu.edu/user/vanhoeve/mdd/)には、多くの貴重なリソースが含まれており、特にINFORMSの記事[Discrete Optimization with Decision Diagrams](http://www.andrew.cmu.edu/user/vanhoeve/papers/discrete_opt_with_DDs.pdf)が参考になります。

## 貢献

さまざまな形の貢献を伴うプルリクエストは大歓迎です。特に、現在のインターフェースを簡素化したり、全体的なパフォーマンスを向上させたり、より多くの問題クラスをカバーするための提案をいただけるとありがたいです。
