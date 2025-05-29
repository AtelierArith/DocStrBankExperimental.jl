```
build_pyhf(load_pyhfjson(path)) -> PyHFModel
```

`expected(αs)`は、長さ`N`のベクトルまたはタプルを受け取る関数であり、ここで`N`は`priors`および`priornames`の長さでもあります。言い換えれば、返されるオブジェクトのこれら3つのフィールドは整列しています。

!!! note
    異なるチャネルからのビンは、`NTuple{Nbins, Vector}`に格納されます。

