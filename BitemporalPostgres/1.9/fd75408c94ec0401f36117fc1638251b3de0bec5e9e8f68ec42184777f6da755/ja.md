delete_component!(r::T, w::Workflow)  where {T<:ComponentRevision}

  * 現在のバージョンのために作成されたコンポーネントを削除します。
  * または、その最新のコンポーネントリビジョンを無効としてマークします。
