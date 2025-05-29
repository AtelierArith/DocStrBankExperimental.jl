```
BoundsCheckCallback(; output_directory="out", save_errors=false, interval=1)
```

[`SubcellLimiterIDP`](@ref)を用いたサブセル制限技術は、特定のローカルまたはグローバルな境界に従うように構築されています。これらの境界が実際に満たされていることを確認するために、このコールバックは境界からの最大偏差を計算します。適用された各境界ごとの最大偏差は、シミュレーションの最後に画面に表示されます。さらに詳しい情報を得るために、`save_errors=true`を設定すると、シミュレーション中の`interval`タイムステップごとに発生したエラーがエクスポートされます。その後、最後のエクスポート以降の最大偏差が"`output_directory`/deviations.txt"に保存されます。`BoundsCheckCallback`は、SSPRK時間積分スキームのステージコールバックとして適用する必要があります。

!!! note
    `SubcellLimiterIDP`の場合、解は事後修正ステージ[`SubcellLimiterIDPCorrection`](@ref)で修正されます。したがって、最終的な解を確認するためには、この境界チェックコールバックは修正ステージの後に呼び出す必要があります。

