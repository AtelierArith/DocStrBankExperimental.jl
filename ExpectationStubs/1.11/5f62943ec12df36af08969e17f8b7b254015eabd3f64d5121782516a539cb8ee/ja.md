```
@expect(defn)
```

スタブを準備し、`defn`に一致する関数呼び出しを期待することを知らせ、結果を返すようにします。

いくつかの形式があり、これらはJuliaの関数宣言に対応しています。例：

  * `@expect(foo(1, 1.5)=10)` これはスタブ`foo`を準備し、入力が`(1, 1.5)`の場合に10を返すようにします。
  * `@expect(foo(3, ::Int)=20)` これはスタブ`foo`を準備し、最初の引数が3で、2番目の引数が任意の`Int`の場合に20を返すようにします。
  * `@expect(foo(5, ::Any)=30)` これはスタブ`foo`を準備し、最初の引数が5で、2番目の引数が任意の型の場合に30を返すようにします。
  * `@expect(foo(Any, ::Any)=40)` これはスタブ`foo`を準備し、2つの引数が与えられた場合に40を返すようにします。

同じスタブに対して、型によって束縛されることを宣言し（つまり、特定の型の任意のものを受け取ることができる）、同じパラメータに対して値によって束縛されることを宣言することはできないことに注意してください。

結果は関数の引数に依存してはならないことに注意してください。これは意図的であり、スタブをシンプルで要点を押さえたものに保つためです。そうすることで、テストをテストする必要がなくなります。

現在、KWArgsはサポートされていません。
