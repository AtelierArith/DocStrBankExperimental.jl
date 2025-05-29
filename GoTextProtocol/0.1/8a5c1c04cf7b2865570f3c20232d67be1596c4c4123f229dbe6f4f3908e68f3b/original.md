gtp_repl(genmove) runs a read-execute-print-loop (REPL) implementing the Go Text Protocol, which calls the user-provided `genmove(board, color, info)` when asked to generate a move.

Go clients that connect to a Julia script will typically expect that script to start a REPL on stdin/stdout, which is the default behaviour for `gtp_repl`. Alternative input/output streams can be specified via the 'input' and 'output' keyword arguments.

The `name` and `version` keyword arguments can be used set the name and version given that are communicated to the client if it asks for them.
