```
bseries(f::Function, order, iterator_type=RootedTreeIterator)
```

指定された`order`までの切り捨てられたB系列を返し、係数は`f`によって決定されます。根付き木のタイプは`iterator_type`によって決定され、`RootedTreeIterator`または`BicoloredRootedTreeIterator`のいずれかになります。`f(t, series)`を呼び出すと、希望する系列の根付き木`t`の係数が型安定な方法で返される必要があります。空の木の場合、`f`は`f(t, nothing)`として呼び出されます。それ以外の場合、これまでに構築された系列が第二引数として渡され、低次の木の値にアクセスできるようになります。

!!! note "基本微分による正規化"
    このメソッドによって返されるB系列の係数は、時間ステップのべき乗を根付き木の`symmetry`で割り、入力ベクトル場$f$の対応する基本微分で掛ける必要があります。詳細は[`evaluate`](@ref)を参照してください。


# 例

平均ベクトル場（AVF）法のB系列は、$b(.) = 1$および$b([t_1, ..., t_n]) = b(t_1)...b(t_n) / (n + 1)$で与えられます。詳細は以下を参照してください。

  * Elena Celledoni, Robert I. McLachlan, David I. McLaren, Brynjulf Owren, G. Reinout W. Quispel, and William M. Wright. "エネルギー保存型ルンゲ・クッタ法。" ESAIM: Mathematical Modelling and Numerical Analysis 43, no. 4 (2009): 645-649. [DOI: 10.1051/m2an/2009020](https://doi.org/10.1051/m2an/2009020)

次のようにしてこれを生成できます。

```jldoctest
julia> series = bseries(3) do t, series
           if order(t) in (0, 1)
               return 1 // 1
           else
               v = 1 // 1
               n = 0
               for subtree in SubtreeIterator(t)
                   v *= series[subtree]
                   n += 1
               end
               return v / (n + 1)
           end
       end
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 5 entries:
  RootedTree{Int64}: Int64[]   => 1
  RootedTree{Int64}: [1]       => 1
  RootedTree{Int64}: [1, 2]    => 1//2
  RootedTree{Int64}: [1, 2, 3] => 1//4
  RootedTree{Int64}: [1, 2, 2] => 1//3
```
