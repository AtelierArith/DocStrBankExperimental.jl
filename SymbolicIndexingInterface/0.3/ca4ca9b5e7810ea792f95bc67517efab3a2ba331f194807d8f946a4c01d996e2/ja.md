```
setp(indp, sym)
```

値プロバイダーと値を受け取り、パラメーター `sym` をその値に設定する関数を返します。`sym` はインデックス、シンボリック変数、または前述のものの配列/タプルである可能性があることに注意してください。

値プロバイダーが [`parameter_values`](@ref) を実装し、返されるコレクションがパラメーターオブジェクトへの可変参照であることが必要です。`parameter_values` がそのような可変参照を返せない場合や、パラメーターを更新する際に追加のアクションを実行する必要がある場合は、[`set_parameter!`](@ref) を実装する必要があります。
