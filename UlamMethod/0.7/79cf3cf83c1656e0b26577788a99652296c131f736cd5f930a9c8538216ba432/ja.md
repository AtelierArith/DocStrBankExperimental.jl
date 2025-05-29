```
struct UlamResult{Dim, M, CRS}
```

主なウラム法計算の結果を格納するコンテナです。

これは、遷移確率行列、関連するビン、および切り離されたビンの3つの主要なコンポーネントで構成されています。

遷移確率行列は次の形式です。

| `P_O2O` | `P_O2ω` | 

| `P_ω2O` |  `0`  |

ここで、`O`は「開いている」（内部）領域を表し、`ω`は「涅槃」（外部）領域を表します。`O`と`ω`の合併は閉じた領域を形成します。

### フィールド

  * `P_O2O`: 図と同様。
  * `P_O2ω`: 図と同様。
  * `P_ω2O`: 図と同様。
  * `binner`: データをビンに分けるために使用される[`BinningAlgorithm`](@ref)。
  * `bins_dis`: データを含んでいたが、最大の強連結成分が取られたときに削除されたビン。

### メソッド

```
P_closed(UlamResult)
```

完全な行列にアクセスします。

```
P_open(UlamResult)
```

`P_O2O`にアクセスします。

```
bins(UlamResult)
```

`bins`にアクセスします。

```
bins_dis(UlamResult)
```

`bins_dis`にアクセスします。

```
membership(data_or_traj, ulam_result)
```

ビン化された領域に対する`data_or_traj`のメンバーシップを計算します。詳細については、[`membership`](@ref)関数を参照してください。

```
counts(data_or_traj, ulam_result)
```

ビン化された領域に対する`data_or_traj`のビンカウントを計算します。詳細については、[`counts`](@ref)関数を参照してください。 ```
