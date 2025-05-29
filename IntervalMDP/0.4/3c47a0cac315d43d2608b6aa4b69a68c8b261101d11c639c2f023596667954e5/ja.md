```
StationaryStrategyConfig
```

定常ポリシーを保存する戦略キャッシュの構成です。新しい選択肢が前のものよりも厳密に優れている場合、戦略は価値反復アルゴリズムの各反復で更新されることに注意してください。これが必要な理由の詳細については、[1, Section 4.3]を参照してください。構成からキャッシュを構築する方法の詳細については、[`construct_strategy_cache`](@ref)を参照してください。

[1] Forejt, Vojtěch, et al. "Automated verification techniques for probabilistic systems." Formal Methods for Eternal Networked Software Systems: 11th International School on Formal Methods for the Design of Computer, Communication and Software Systems, SFM 2011, Bertinoro, Italy, June 13-18, 2011. Advanced Lectures 11 (2011): 53-113.
