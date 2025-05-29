```
@interior_qf name=def
```

ユーザー定義の内部（体積）Q関数を作成し、それを `name` という名前の変数に割り当てます。Q関数の定義は次のようになります：

```
@interior_qf user_qf=(
    ceed::CEED,
    [const1=val1, const2=val2, ...],
    [ctx::ContextType],
    (I1, :in, EvalMode, dims...),
    (I2, :in, EvalMode, dims...),
    (O1, :out, EvalMode, dims...),
    body
)
```

`const=val` の形式の定義は、Q関数内でコンパイル時定数となる定義に使用されます。たとえば、`dim` が問題の次元に設定された変数である場合、`dim=dim` はQ関数の本体内でコンパイル時定数として `dim` を利用可能にします。

ユーザーがQ関数にコンテキスト構造体を提供したい場合は、オプションで `ctx::ContextType` を含めることで実現できます。ここで `ContextType` はコンテキスト構造体の型であり、`ctx` はQ関数の本体内でバインドされる名前です。

次に、入力および出力配列の定義が続きます。これらは `(arr_name, (:in|:out), EvalMode, dims...)` の形式を取ります。各配列は `arr_name` という名前の変数にバインドされます。入力配列は :in でタグ付けされ、出力配列は :out でタグ付けされるべきです。`EvalMode` を指定し、その後に配列の次元を続けます。配列がスカラー（Q点ごとに1つの数）で構成されている場合、`dims` は省略するべきです。

# 例

  * 質量演算子の「Qデータ」を計算するためのQ関数。これは、重み付き積分の重みとヤコビアンの行列式によって与えられます。メッシュのヤコビアン（ノードメッシュポイントの勾配）と重み付き積分の重みは入力配列として与えられ、Qデータは出力配列です。`dim` はコンパイル時定数として与えられ、したがって配列 `J` は静的にサイズ指定され、したがって `det(J)` は与えられた次元に対して最適化された実装に自動的にディスパッチされます。

```
@interior_qf build_qfunc = (
    ceed, dim=dim,
    (J, :in, EVAL_GRAD, dim, dim),
    (w, :in, EVAL_WEIGHT),
    (qdata, :out, EVAL_NONE),
    qdata[] = w*det(J)
)
```
