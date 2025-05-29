```
serve_sync(port=3000, shared=false, print_stack=true, async=false)
```

Run the daemon, running all files and expressions sended by the client function.

# Optionals

  * port: port to listen (default=3000).
  * shared: Share the environment between calls. If it is false (default) each run has its own environment, so the variables/functions are not shared.
  * print_stack: Print the complete stack when there is an error. By default it is true.
  * async: Run the clients in different clients at the same time.
  * threaded: Run each client in a new thread (true by default if async is true).
