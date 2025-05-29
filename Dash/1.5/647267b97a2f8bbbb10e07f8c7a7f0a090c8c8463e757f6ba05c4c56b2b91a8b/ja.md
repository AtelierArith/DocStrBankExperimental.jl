```
dcc_location(;kwargs...)
```

現在のwindow.locationオブジェクトを更新し、window.historyの状態を追跡するLocationコンポーネントです。複数のページを持つアプリを作成するために、`dash_core_components.Link`コンポーネントと一緒に使用します。

  * `id` (String; 必須): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

このIDは、アプリ内のすべてのコンポーネントで一意である必要があります。

  * `hash` (String; オプション): window.locationのハッシュ - 例: "#myhash"
  * `href` (String; オプション): window.locationのhref - 例: "/my/full/pathname?myargument=1#myhash"
  * `pathname` (String; オプション): window.locationのパス名 - 例: "/my/full/pathname"
  * `refresh` ('callback-nav' | Bool; オプション): `True`を使用してDashアプリの外にナビゲートするか、ページを手動で更新します。

同じコールバックがLocationコンポーネントを更新し、ページコンテンツも更新する場合は`False`を使用します - 通常、Pagesを使用しないマルチページアプリで使用されます。コールバック内でURLを更新している場合、または異なるコールバックが新しいLocationに応じて更新されたコンテンツで応答する場合は'callback-nav'を使用します。これは、Pagesを使用するマルチページアプリで一般的です。これにより、ページを更新せずに新しいページにナビゲートできます。

  * `search` (String; オプション): window.locationの検索 - 例: "?myargument=1"
