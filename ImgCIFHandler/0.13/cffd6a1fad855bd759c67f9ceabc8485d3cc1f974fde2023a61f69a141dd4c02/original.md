In order to access images, an archive must be specified, and then supplied to the `imgload` routine. To avoid re-downloading on each call, this archive should be created separately.

An archive is either remote, or local. A local archive may have a remote equivalent, such that it is a cached version. We provide routines to convert from remote to local, which involves downloading selected files.
