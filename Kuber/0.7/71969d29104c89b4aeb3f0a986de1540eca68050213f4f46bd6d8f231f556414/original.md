Fetch logs of the specified Pod

Parameters:

  * name::String (required)

Keyword Args:

  * container::String : The container for which to stream logs. Defaults to only container if there is one container in the pod.
  * follow::Bool : Follow the log stream of the pod. Defaults to false.
  * limitBytes::Int32 : If set, the number of bytes to read from the server before terminating the log output. This may not display a complete final line of logging, and may return slightly more or slightly less than the specified limit.
  * pretty::String : If 'true', then the output is pretty printed.
  * previous::Bool : Return previous terminated container logs. Defaults to false.
  * sinceSeconds::Int32 : A relative time in seconds before the current time from which to show logs. If this value precedes the time a pod was started, only logs since the pod start will be returned. If this value is in the future, no logs will be returned. Only one of sinceSeconds or sinceTime may be specified.
  * sinceTime::String : An RFC3339 timestamp from which to show logs. If this value precedes the time a pod was started, only logs since the pod start will be returned. If this value is in the future, no logs will be returned. Only one of sinceSeconds or sinceTime may be specified.
  * tailLines::Int32 : If set, the number of lines from the end of the logs to show. If not specified, logs are shown from the creation of the container or sinceSeconds or sinceTime
  * timestamps::Bool : If true, add an RFC3339 or RFC3339Nano timestamp at the beginning of every line of log output. Defaults to false.

Returns: String of all log entries, one per line
