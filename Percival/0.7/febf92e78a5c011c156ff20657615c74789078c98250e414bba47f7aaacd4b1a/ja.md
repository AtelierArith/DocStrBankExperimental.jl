```
update_cx!(nlp, x)
```

`AugLagModel`が与えられた場合、`x != nlp.x` であれば、`nlp.model` の `cons` を呼び出して内部値 `nlp.cx` を更新し、`nlp.fx` を NaN にリセットします。また、`nlp.μc_y` も更新します。
