複数のロガーにログイベントをリダイレクトします。主な使用ケースは、ファイルとコンソールの両方にログを記録できるようにすることです。副次的には、すべてのログメッセージのカウントを追跡できます。

# 例

```Julia
MultiLogger([TerminalLogger(stderr), SimpleLogger(stream)], LogEventTracker())
```
