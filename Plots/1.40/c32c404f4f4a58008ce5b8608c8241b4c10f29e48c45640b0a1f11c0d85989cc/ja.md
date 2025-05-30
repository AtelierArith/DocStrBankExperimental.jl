バックエンドとデフォルトの一時的な設定を許可します。設定は `do` ブロックのみに適用されます。例:

```
Plots.with(:gr, size=(400,400), type=:histogram) do
  plot(rand(10))
  plot(rand(10))
end
```
