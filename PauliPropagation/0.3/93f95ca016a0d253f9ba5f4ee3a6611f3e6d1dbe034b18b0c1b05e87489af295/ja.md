```
mergeandempty!(psum, aux_psum)
```

`aux_psum`を`psum`に`merge`関数を使用してマージします。`merge`は異なる係数タイプに対してオーバーロードできます。その後、次のイテレーションのために`aux_psum`を空にします。
