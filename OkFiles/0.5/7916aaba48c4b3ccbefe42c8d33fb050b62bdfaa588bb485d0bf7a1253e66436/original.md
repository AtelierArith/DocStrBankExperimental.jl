`filelist(dir::SFTPClient.SFTP [, subdir])` returns the file list for the SFTP directory. This function utilize `Base.readdir(sftp::SFTP, join::Bool = false, sort::Bool = true)` of `SFTPClient`.

This function currently do no support `join` and `sort` argument, because it rely on `sftpstat` to check whether a path is a file, but `sftpstat` always returns unsorted and not-joined results.
