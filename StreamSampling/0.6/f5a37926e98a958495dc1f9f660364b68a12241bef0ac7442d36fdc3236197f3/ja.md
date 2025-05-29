# StreamSampling.jl

[![CI](https://github.com/JuliaDynamics/StreamSampling.jl/workflows/CI/badge.svg)](https://github.com/JuliaDynamics/StreamSampling.jl/actions?query=workflow%3ACI) [![](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliadynamics.github.io/StreamSampling.jl/stable/) [![codecov](https://codecov.io/gh/JuliaDynamics/StreamSampling.jl/graph/badge.svg?token=F8W0MC53Z0)](https://codecov.io/gh/JuliaDynamics/StreamSampling.jl) [![Aqua QA](https://raw.githubusercontent.com/JuliaTesting/Aqua.jl/master/badge.svg)](https://github.com/JuliaTesting/Aqua.jl) [![DOI](https://zenodo.org/badge/692407431.svg)](https://zenodo.org/doi/10.5281/zenodo.12826684)

このパッケージの範囲は、ストリーム内のアイテム数が不明な場合でも、データを一度の通過でサンプリングする一般的な方法を提供することです。

これは他のサンプリング手続きに対していくつかの利点があります：

  * イテラブルが遅延評価の場合、必要なメモリは小さな定数であるか、サンプルのサイズに関連して増加します。全体の母集団に対してではありません。
  * リザーバー法を使用すると、収集されたサンプルは、サンプリングプロセスの任意の時点でこれまでに見たストリームの部分のランダムサンプルです。
  * このライブラリに実装された技術を使用したサンプリングは、アイテムの母集団を事前にメモリに保存する必要がないため、かなりのパフォーマンス向上をもたらす場合があります。

利用可能な機能についての情報は、[ドキュメント](https://juliadynamics.github.io/StreamSampling.jl/stable/)を参照してください。

## 貢献

貢献は大歓迎です！問題に遭遇した場合、改善の提案がある場合、または新しい機能を追加したい場合は、気軽にイシューを開くか、プルリクエストを提出してください。
