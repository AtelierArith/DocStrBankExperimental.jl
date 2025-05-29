`DELE`: 離散オイラー・ラグランジュ方程式

離散オイラー・ラグランジュ方程式は、次の形の初期値問題を定義します。

$$
D_1 L_d (q_{n}, q_{n+1}) + D_2 L_d (q_{n-1}, q_{n}) = 0 ,
$$

ここで、$L_d$は離散ラグランジアンです。

### パラメータ

  * `LdType <: Callable`: `Ld`の型
  * `D1LdType <: Callable`: `D1Ld`の型
  * `D2LdType <: Callable`: `D2Ld`の型
  * `invType <: OptionalInvariants`: 不変量の型
  * `parType <: OptionalParameters`: パラメータの型
  * `perType <: OptionalPeriodicity`: 周期性の型

### フィールド

  * `Ld`: 離散ラグランジアンを計算する関数
  * `D1Ld`: 第一引数に関する離散ラグランジアンの導関数を計算する関数
  * `D2Ld`: 第二引数に関する離散ラグランジアンの導関数を計算する関数
  * `invariants`: 不変量の計算のための関数、方程式の不変量を含む`NamedTuple`または`NullInvariants`
  * `parameters`: パラメータの型制約、方程式のパラメータを含む`NamedTuple`または`NullParameters`
  * `periodicity`: 周期的解を切るための状態ベクトル`q`の周期性を決定する、`AbstractArray`または`NullPeriodicity`

### コンストラクタ

```julia
DELE(Ld, D1Ld, D2Ld, invariants, parameters, periodicity)
DELE(Ld, D1Ld, D2Ld; invariants = NullInvariants(), parameters = NullParameters(), periodicity = NullPeriodicity())
```

### 関数定義

離散ラグランジアンを提供する関数`Ld`は、次のインターフェースを持たなければなりません。

```julia
function Ld(t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    return ...
end
```

ここで、`t_{n}`と`t_{n+1}`は前のステップと次のステップの時間、`q_{n}`と`q_{n+1}`は前のステップと次のステップの解ベクトル、`params`はラグランジアンが依存する可能性のある追加のパラメータの`NamedTuple`です。離散ラグランジアンの第一引数および第二引数に関する導関数、`D_1 L_d`および`D_2 L_d`は、それぞれ次のインターフェースを持たなければなりません。

```julia
function D1Ld(D, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D1[1] = ...
    D1[2] = ...
    ...
end
```

および

```julia
function D2Ld(D2, t_{n}, t_{n+1}, q_{n}, q_{n+1}, params)
    D2[1] = ...
    D2[2] = ...
    ...
end
```
