```
simulate!(mechanism, tend, args..., kwargs)
```

`mechanism`を`tend`秒間シミュレートします。時間ステップはmechanismで設定されています。

コントローラーまたは制御関数（[`Controller`](@ref)を参照）を`args`で渡すことができます。コントローラーが必要ない場合は、何も渡す必要はありません。

利用可能なkwargs:

  * `record`:     状態の軌跡を保存するかどうかを指定します（`true`）または保存しない（`false`）。
  * `ε`:          ソルバーの許容誤差。
