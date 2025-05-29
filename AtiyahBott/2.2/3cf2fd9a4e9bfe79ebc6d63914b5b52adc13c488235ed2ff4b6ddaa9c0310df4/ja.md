```
AtiyahBottFormula(n, d, m, P; do_check, show_bar)
```

アティヤ-ボット残差定理をクラス `P` に適用します。これは、次元 `n` の射影空間への有理マークされた安定写像のモジュライ空間におけるもので、次数 `d` で `m` のマークがあります。

# 引数

  * `n::Int64`: 射影空間の次元。
  * `d::Int64`: 安定写像の次数、正でなければなりません。
  * `m::Int64`: マークの数。
  * `P`: 等変クラス。
  * `do_check::Bool`: `true` の場合、`P` が適切に定義されたゼロサイクルであるかをチェックし、そうでない場合は計算を停止します。`false` の場合、計算は予期しない動作をする可能性があります。デフォルトは `true` です。
  * `show_bar::Bool`: この条件が `false` の場合のみ進捗バーを非表示にします。デフォルトは `true` です。

`P` の一般的な構成は次のとおりです。

```julia-repl
julia> P = 
```

`=` の後には、等変クラスの式を書く必要があります。この式は等変クラスの組み合わせです。`P` の次数は次のように計算します。

```julia-repl
julia> AtiyahBottFormula(n, d, m, P);
```

# 例

```julia-repl
julia> P = Hypersurface(5);
julia> AtiyahBottFormula(3, 1, 0, P);
Warning: the class is not a 0-cycle.
julia> AtiyahBottFormula(4, 1, 0, P);
Result: 2875
julia> AtiyahBottFormula(4, 1, 0, P, do_check = false); #`P` の事前チェックをスキップ
julia> AtiyahBottFormula(4, 1, 0, P, show_bar = false); #進捗バーは表示されません
```

この関数は、`P` と同じ次元の配列を返します（非ベクトル化クラスは1次元配列と見なされます）。配列にアクセスするためのJuliaの表記法は `name_of_array[i]` で、`i` は1から始まるインデックスです。

# 例

```julia-repl
julia> P = Incidency(2)*Hypersurface(3);
julia> x = AtiyahBottFormula(3, 2, 0, P)[1];
Result: 81
julia> x
81
```

クラス `P` はパラメータをサポートしています。

```julia-repl
julia> P = Hypersurface(3)*(Incidency(2)//3)^(d-1);
julia> d = 2;
julia> AtiyahBottFormula(3, d, 0, P);
Result: 27
julia> d = 3;
julia> AtiyahBottFormula(3, d, 0, P);
Result: 84
```

等変クラスのサポートに関するさらなる例が利用可能です。`?` を入力し、その後にクラスの名前を入力するだけで十分です。現在サポートされているクラスは次のとおりです：

  * `O1_i(j)`         (Euler class of $\mathrm{ev}_j^*\mathcal{O}_{\mathbb{P}^n}(1)$)
  * `O1()`            (product of all `O1_i`)
  * `Psi(a)`          (cycle of $\psi$-classes)
  * `Jet(p,q)`        (Euler class of the jet bundle $J^p$ of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(q)$)
  * `Hypersurface(b)` (Euler class of the direct image of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(b)$)
  * `Incidency(r)`    (cycle parameterizing curves meeting a linear subspace of codimension $r$)
  * `Contact()`       (cycle parameterizing contact curves)
  * `R1(k)`           (first derived functor of direct image of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(-k)$)

クラスを追加するには、著者に連絡してください。
