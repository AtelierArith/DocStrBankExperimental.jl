```
writeframe(io::CSeis, trcs, idx...)
```

`io`にフレームを書き込みます。フレームの位置は`idx...`から決定され、整数または`CartesianIndex`のいずれかです。`idx...`から最小限のヘッダーが作成され、`io`にも書き込まれます。
