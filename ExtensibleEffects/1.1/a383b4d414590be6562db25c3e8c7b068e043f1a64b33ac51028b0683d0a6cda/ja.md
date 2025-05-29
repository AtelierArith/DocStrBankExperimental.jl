```
@runhandlers handlers eff
```

便利のために、`runhandlers` 関数をマクロとしても提供します。

これにより、`@syntax_eff` 自動実行からの残りのハンドラーをより簡単に実行できます。

## 例

```
@runhandlers WithCall(args, kwargs) @syntax_eff begin
  a = Callable(x -> 2x)
  @pure a
end
```
