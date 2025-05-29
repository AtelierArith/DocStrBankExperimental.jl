```
selection!(norm_weights, s_t1_temp, s_t_nontemp, ϵ_t;
    resampling_method = :multinomial)
```

`norm_weights`を使用して粒子を再サンプリングします。この関数は`s_t1_temp`、`s_t_nontemp`、および`ϵ_t`をその場で変更します。
