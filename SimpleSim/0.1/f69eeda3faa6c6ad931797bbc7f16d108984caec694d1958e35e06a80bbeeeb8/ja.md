```
print_model_tree(model; io = stdout)
```

与えられたモデルの*ツリー*を印刷します。これは、Linuxの`tree`コマンドによって印刷されるフォルダツリーに似ています。

フィードバック制御された倒立振子の例は次のようになります。

```
julia> print_model_tree(my_model)
└─1 (TypeCT): top-level model / FeedbackSystem
  ├─2 (TypeCT): .inverted_pendulum / NamedTuple
  └─3 (TypeCT): .controller / NamedTuple
```

まず、`model_id`が示され、その後にタイプ（`TypeCT`、`TypeDT`または`TypeHybrid`）が続きます。次に、スーパーモデル内の各モデルの名前が続きます。これは、`models`として渡された`NamedTuple`内のフィールド名であるか、ベクターまたはタプルの場合はインデックスです。最後に、スラッシュの後に各モデルのタイプが示されます。これは、`struct`タイプの名前または`NamedTuple`である必要があります。

次のように、自分のIOストリームを`print_model_tree`に渡すこともできます。

```julia
print_model_tree(my_buffer, model)
```
