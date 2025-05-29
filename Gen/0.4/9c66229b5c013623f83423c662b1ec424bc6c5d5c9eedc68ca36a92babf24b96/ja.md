ProductDistribution(distributions::Vararg{<:Distribution})

与えられた非空の分布リストの積である新しい分布を定義します。これらの分布は共通の型を持っています。

引数は基本分布のリストで構成されています。

例:

```julia
normal_strip = ProductDistribution(uniform, normal)
```

結果として得られる積分布は `n` 引数を取り、ここで `n` はリスト内の各分布が取る引数の数の合計です。これらの引数は、コンストラクタに渡される分布の順序で、各コンポーネント分布への引数です。

例:

```julia
@gen function unit_strip_and_near_seven()
    x ~ flip_and_number(0.0, 0.1, 7.0, 0.01)
end
```
