```julia
struct HomotopyNonlinearFunction{iip, specialize, F, P, Q, D} <: SciMLBase.AbstractNonlinearFunction{iip}
```

多項式非線形方程系の表現であり、次のように与えられます。

$$
0 = f(polynomialize(u, p), p)
$$

HomotopyContinuationを使用して解くために設計されています。

## コンストラクタ

関数 `f` のみが必要であることに注意してください。この関数は `f!(du,u,p)` または `du = f(u,p)` として与えられるべきです。インプレースとアウトオブプレースの処理に関する詳細は、`iip` のセクションを参照してください。

ヤコビ行列関数などを提供するために、`f` は必要なフィールドが埋められた [`NonlinearFunction`](@ref) でなければなりません。

## iip: インプレース vs アウトオブプレース

この引数に関する詳細は、ODEFunctionのドキュメントを参照してください。

## specialize: コンパイルと特殊化の制御

この引数に関する詳細は、ODEFunctionのドキュメントを参照してください。

## フィールド

`HomotopyNonlinearFunction` 型のフィールドは、入力の名前と直接一致します。

  * `f`: 多項式関数 `f`。`NonlinearFunction{iip, specialize}` として保存されます。コンストラクタに `NonlinearFunction` として提供されない場合は、適切にラップされます。
  * `polynomialize`: 非線形系は非多項式関数の多項式である場合があります。例えば、

    $$
    sin^2(x^2) + 2sin(x^2) + 1 = 0
    log(x + y) ^ 3 = 0.5
    $$

    は `[sin(x^2), log(x + y)]` の多項式です。このような系を許可するために、`polynomialize` は元の系の状態ベクトル（「元の空間」ベクトルと呼ばれる）を多項式系の状態ベクトル（「多項式空間」ベクトルと呼ばれる）に変換します。上記の例では、次の関数になります。

    ```julia
    function polynomialize(u, p)
      x, y = u
      return [sin(x^2), log(x + y)]
    end
    ```

    `[x, y]` を「元の空間」に、`[sin(x^2), log(x + y)]` を「多項式空間」にあると呼びます。

    これはデフォルトで `u` をそのまま返す関数になります。
  * `unpolynomialize`: `polynomialize` の逆操作です。

    この関数は「多項式空間」にあるベクトル `u′` を入力として受け取り、「元の空間」にあるベクトルのコレクション `uᵢ ∀ i ∈ {1..n}` を返します。ここで `polynomialize(uᵢ, p) == u′ ∀ i` です。マッピングが単射でない場合があるため、コレクションが返されます。無限のベクトル `uᵢ` を持つ周期関数の場合、どのベクトルを返すかはユーザーの選択に委ねられます。

    `polynomialize` の前述の例では、この関数は次のようになります。

    ```julia
    function unpolynomialize(u, p)
      a, b = u
      return [
        [sqrt(asin(a)), exp(b) - sqrt(asin(a))],
        [-sqrt(asin(a)), exp(b) + sqrt(asin(a))],
      ]
    end
    ```

    `sin` の存在により、このような関数は無限に存在します。この例では、区間 `[-π/2, π/2]` 内の根を返すことを選択しています。
  * `denominator`: `denominator(u, p) -> denoms` の形の関数で、`denoms` はゼロにならない分母項の配列です。これは、`f` が有理関数の分子を表す場合に便利です。`denoms` のいずれかの値が閾値を下回る原因となる `f` の根は除外されます。ここで `u` は「多項式空間」にある必要があることに注意してください。
