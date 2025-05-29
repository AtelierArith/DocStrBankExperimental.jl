```
plot_front(designs; grad=cgrad(:Paired_12), xlabel, ylabel, labels=get_labels(designs))
```

効率的なデザインの散布図を描画します。これは `efficient_designs` から返されます。

オプションで、色のグラデーションを指定して、色を描画することができます。

# 例

```julia
designs = efficient_designs(experiment, state)
plot_front(designs)
plot_front(designs; grad = cgrad(:Paired_12))
```
