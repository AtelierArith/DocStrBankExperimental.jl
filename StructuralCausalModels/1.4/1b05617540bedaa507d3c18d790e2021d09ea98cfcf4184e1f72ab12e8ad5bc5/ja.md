# DAG

有向非巡回グラフコンストラクタ

```julia
DAG(name, model; df)

```

### 必須引数

```julia
* `name::AbstractString`               : DAGオブジェクトの名前
* `d::ModelDefinition`                 : DAG定義
```

ここで

```
ModelDefinition = Union{OrderedDict, AbstractString, NamedArray}
```

使用例については拡張ヘルプを参照してください。

### キーワード引数

```julia
* `df::DataFrame`                      : 観察データを含むDataFrame
```

### 戻り値

```julia
* `dag::DAG`                           : テストのブール結果
```

# 拡張ヘルプ

OrderedDictの定義では、回帰モデルでは`=>`を`~`、因果モデルでは`<-`として読み取ります。例えば：

```julia
d = OrderedDict(
  :u => [:x, :v],
  :s1 => [:u],
  :w => [:v, :y],
  :s2 => [:w]
);
dag = DAG("my_name", d)
```

Rのdagittyからの例：

amat <- dagitty("dag { {X V} -> U; S1 <- U; {Y V} -> W; S2 <- W}”)

```julia
dag = DAG("my_name", "dag { {X V} -> U; S1 <- U; {Y V} -> W; S2 <- W}”)
display(dag) # DAGを表示
```

Rのggmからの例：

amat <- DAG(U~X+V, S1~U, W~V+Y, S2~W, order=FALSE)

```julia
dag = DAG("my_name", "DAG(U~X+V, S1~U, W~V+Y, S2~W”)
display(dag) # DAGを表示
```

### 謝辞

元の著者：                       Giovanni M. Marchetti

Juliaへの翻訳：                   Rob J Goedman

### ライセンス

Rパッケージggmはライセンス：GPL-2の下でライセンスされています。

Juliaの翻訳は：MITの下でライセンスされています。

APIの一部、エクスポートされています。
