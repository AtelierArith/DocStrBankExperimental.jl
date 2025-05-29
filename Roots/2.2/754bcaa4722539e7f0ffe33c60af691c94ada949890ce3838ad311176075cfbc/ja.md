```
Order0()
```

`Order0` メソッドは、他の導関数なしの根探索法に対する、より堅牢であるが、可能性としては遅い代替手段として設計されています。この実装は、*Personal Calculator Has Key to Solve Any Equation $f(x) = 0$* に記載されているアルゴリズムに大まかに従っています。これは、[HP-34C](http://www.hpl.hp.com/hpjournal/pdfs/IssuePDFs/1979-12.pdf) の SOLVE ボタンです。基本的なアイデアは、セカントステップを使用することです。途中でブラケットが見つかった場合は、`AlefeldPotraShi` を使用してブラケットアルゴリズムに切り替えます。セカントステップが関数値を減少させることに失敗した場合、最大で $4$ 回まで二次ステップが使用されます。

これは実際には $0$ 次ではありません：セカント法は次数 $1.6...$ です [Wikipedia](https://en.wikipedia.org/wiki/Secant_method#Comparison_with_other_root-finding_methods) し、ブラケット法は次数 $1.6180...$ です [Wikipedia](http://www.ams.org/journals/mcom/1993-61-204/S0025-5718-1993-1192965-2/S0025-5718-1993-1192965-2.pdf) ので、合理的なスタートポイントと関数に対して、このアルゴリズムは超線形であり、非合理的なスタートポイントに対しても比較的堅牢であるはずです。
