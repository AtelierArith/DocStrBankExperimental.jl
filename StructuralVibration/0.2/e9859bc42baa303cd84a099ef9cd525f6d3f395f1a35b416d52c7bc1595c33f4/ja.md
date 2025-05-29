```
solve(prob::StateSpaceFRFProblem; type = :dis, ismat = false, progress = true)
solve(prob::StateSpaceModalFRFProblem; type = :dis, ismat = false, progress = true)
```

直接法またはモーダル法によってFRF行列を計算します

**入力**

  * `prob`: 問題データを含む構造体
  * `type`: 計算するFRFのタイプ

      * `:dis`: アドミタンス
      * `:vel`: モビリティ
      * `:acc`: 加速度
  * `ismat`: FRF行列を3D配列として返す（デフォルト = false）
  * `progress`: 進行状況バーを表示する（デフォルト = true）

**出力**

  * `sol`: FRFSolution構造体

      * `u`: FRF行列
