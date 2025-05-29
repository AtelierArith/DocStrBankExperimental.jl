A file writer that implements the `IO` interface, but only provides `write` methods.

Constructor parameters:

  * filename: name (including path) of file to log into
  * sizelimit: size of file (in bytes) after which the file should be rotated
  * nfiles: number of rotated files to maintain
