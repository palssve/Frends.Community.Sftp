# Frends.Community.Sftp

Frends Community Tasks for Sftp servers.

[![Actions Status](https://github.com/CommunityHiQ/Frends.Community.Sftp/workflows/PackAndPushAfterMerge/badge.svg)](https://github.com/CommunityHiQ/Frends.Community.Sftp/actions) ![MyGet](https://img.shields.io/myget/frends-community/v/Frends.Community.Sftp) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 

- [Installing](#installing)
- [Tasks](#tasks)
     - [ListDirectory](#ListDirectory)
     - [Delete](#Delete)
     - [ReadText](#ReadText)
     - [ReadBytes](#ReadBytes)
     - [WriteText](#WriteText)
     - [WriteBytes](#WriteBytes)
- [Building](#building)
- [Contributing](#contributing)
- [Change Log](#change-log)

# Installing

You can install the Task via frends UI Task View or you can find the NuGet package from the following NuGet feed
https://www.myget.org/F/frends-community/api/v3/index.json and in Gallery view in MyGet https://www.myget.org/feed/frends-community/package/nuget/Frends.Community.Sftp

# Tasks

## ListDirectory

Gets directory and file listing of a SFTP server.

### Parameters

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| Server | `string` | Server address. | `sftp.example.com` |
| Port | `int` | Port number. | `22` |
| UserName | `string` | User name. | `username` |
| Password | `string` | Password. | `secret` |
| Directory | `string` | Directory on the server. | `/documents` |

### Options

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| IncludeType | `Enum (File, Directory, Both)` | Types to include in the directory listing. | `File` |
| FileMask | `string` | File mask, supports wildcards. | `*.jpg` |
| IncludeSubdirectories | `bool` | If set to yes, a recursive search is performed to include the contents of subdirectories. |  |
| PrivateKeyFileName | `string` | Full path to private key file. Supports RSA and DSA private key in both OpenSSH and ssh.com format. | `C:\private.key` |
| Passphrase | `string` | Passphrase for the private key file. |  |
| Delimiter | `Passphrase` | Passphrase for the private key file. | `secret` |
| UseKeyboardInteractiveAuthenticationMethod | `bool` | Enable keyboard-interactive authentication | `Yes` |

### Returns

Result is a list of objects with following parameters.

| Property | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| FullPath | `string` | Full path of directory or file. | `/documents/image01.jpg` |
| IsDirectory | `bool` | Value indicating whether file representing a directory. | `false` |
| IsFile | `bool` | Value indicating whether file representing a file. | `true` |
| Length | `long` | File size in bytes. | `12345` |
| Name | `string` | Name of directory or file. | `image01.jpg` |
| LastAccessTimeUtc | `DateTime` | DateTime in UTC time for the last time file/directory was accessed. | |
| LastWriteTimeUtc | `DateTime` | DateTime in UTC time for the last time file/directory was written to. | |
| LastAccessTime | `DateTime` | DateTime in local time for the last time file/directory was accessed. | |
| LastWriteTime | `DateTime` | DateTime in local time for the last time file/directory was written to. | |

## Delete

deletes a file on  a SFTP server.

### Parameters

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| Server | `string` | Server address. | `sftp.example.com` |
| Port | `int` | Port number. | `22` |
| UserName | `string` | User name. | `username` |
| Password | `string` | Password. | `secret` |
| Directory | `string` | -not used- | `` |
| Path | `string` | FullPath of the file to be deleted on the server  | `sftpuser/data.json` |

### Options

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| IncludeType | `Enum (File, Directory, Both)` | - not used - | `File` |
| FileMask | `string` | - not used -| `*.jpg` |
| IncludeSubdirectories | `bool` | - not used - |  |
| PrivateKeyFileName | `string` | Full path to private key file. Supports RSA and DSA private key in both OpenSSH and ssh.com format. | `C:\private.key` |
| Passphrase | `string` | Passphrase for the private key file. |  |
| Delimiter | `Passphrase` | Passphrase for the private key file. | `secret` |
| UseKeyboardInteractiveAuthenticationMethod | `bool` | Enable keyboard-interactive authentication | `Yes` |

### Returns

Nothing

## ReadText

Get Text contents of a file on the SFTP server

### Parameters

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| Server | `string` | Server address. | `sftp.example.com` |
| Port | `int` | Port number. | `22` |
| UserName | `string` | User name. | `username` |
| Password | `string` | Password. | `secret` |
| Directory | `string` | -not used- | `` |
| Path | `string` | FullPath of the file to be read  | `sftpuser/data.json` |

### Options

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| IncludeType | `Enum (File, Directory, Both)` | - not used - | `File` |
| FileMask | `string` | - not used -| `*.jpg` |
| IncludeSubdirectories | `bool` | - not used - |  |
| PrivateKeyFileName | `string` | Full path to private key file. Supports RSA and DSA private key in both OpenSSH and ssh.com format. | `C:\private.key` |
| Passphrase | `string` | Passphrase for the private key file. |  |
| Delimiter | `Passphrase` | Passphrase for the private key file. | `secret` |
| UseKeyboardInteractiveAuthenticationMethod | `bool` | Enable keyboard-interactive authentication | `Yes` |
| FileEncoding                                | Enum           | Encoding for the read content. By selecting 'Other' you can use any encoding. | |
| EncodingInString                            | string         | The name of encoding to use. Required if the FileEncoding choice is 'Other'. A partial list of supported encoding names: https://msdn.microsoft.com/en-us/library/system.text.encoding.getencodings(v=vs.110).aspx | `iso-8859-1` |


### Returns

String containing the file contents. 


## ReadBytes

Reads Byte array content of file on the SFTP server

### Parameters

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| Server | `string` | Server address. | `sftp.example.com` |
| Port | `int` | Port number. | `22` |
| UserName | `string` | User name. | `username` |
| Password | `string` | Password. | `secret` |
| Directory | `string` | -not used- | `` |
| Path | `string` | FullPath of the file to be read on the server  | `sftpuser/data.json` |

### Options

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| IncludeType | `Enum (File, Directory, Both)` | - not used - | `File` |
| FileMask | `string` | - not used -| `*.jpg` |
| IncludeSubdirectories | `bool` | - not used - |  |
| PrivateKeyFileName | `string` | Full path to private key file. Supports RSA and DSA private key in both OpenSSH and ssh.com format. | `C:\private.key` |
| Passphrase | `string` | Passphrase for the private key file. |  |
| Delimiter | `Passphrase` | Passphrase for the private key file. | `secret` |
| UseKeyboardInteractiveAuthenticationMethod | `bool` | Enable keyboard-interactive authentication | `Yes` |


### Returns

byte array  `byte []` containing the file contents. 


## WriteText

Write Text content to a  file on the SFTP server

### Parameters

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| Server | `string` | Server address. | `sftp.example.com` |
| Port | `int` | Port number. | `22` |
| UserName | `string` | User name. | `username` |
| Password | `string` | Password. | `secret` |
| Directory | `string` | -not used- | `` |
| Content | `string` | Text content to be writte ... | `Jaa jaa` |
| Path | `string` | FullPath to the  file to be written  | `sftpuser/data.txt` |


### Options

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| IncludeType | `Enum (File, Directory, Both)` | - not used - | `File` |
| FileMask | `string` | - not used -| `*.jpg` |
| IncludeSubdirectories | `bool` | - not used - |  |
| PrivateKeyFileName | `string` | Full path to private key file. Supports RSA and DSA private key in both OpenSSH and ssh.com format. | `C:\private.key` |
| Passphrase | `string` | Passphrase for the private key file. |  |
| Delimiter | `Passphrase` | Passphrase for the private key file. | `secret` |
| UseKeyboardInteractiveAuthenticationMethod | `bool` | Enable keyboard-interactive authentication | `Yes` |
| FileEncoding                                | Enum           | Encoding for the read content. By selecting 'Other' you can use any encoding. | |
| EncodingInString                            | string         | The name of encoding to use. Required if the FileEncoding choice is 'Other'. A partial list of supported encoding names: https://msdn.microsoft.com/en-us/library/system.text.encoding.getencodings(v=vs.110).aspx | `iso-8859-1` |


### Returns

Nothing


## WriteBytes

Write byte array content to a  file on the SFTP server

### Parameters

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| Server | `string` | Server address. | `sftp.example.com` |
| Port | `int` | Port number. | `22` |
| UserName | `string` | User name. | `username` |
| Password | `string` | Password. | `secret` |
| Directory | `string` | -not used- | `` |
| Content | `byte []` | byte array to be written ... | `0x12324...`  |
| Path | `string` | FullPath to the  file to be written  | `sftpuser/data.txt` |


### Options

| Name | Type | Description | Example |
| -------- | -------- | -------- | -------- |
| IncludeType | `Enum (File, Directory, Both)` | - not used - | `File` |
| FileMask | `string` | - not used -| `*.jpg` |
| IncludeSubdirectories | `bool` | - not used - |  |
| PrivateKeyFileName | `string` | Full path to private key file. Supports RSA and DSA private key in both OpenSSH and ssh.com format. | `C:\private.key` |
| Passphrase | `string` | Passphrase for the private key file. |  |
| Delimiter | `Passphrase` | Passphrase for the private key file. | `secret` |
| UseKeyboardInteractiveAuthenticationMethod | `bool` | Enable keyboard-interactive authentication | `Yes` |


### Returns

Nothing


# Building

Clone a copy of the repository

`git clone https://github.com/CommunityHiQ/Frends.Community.Sftp.git`

Rebuild the project

`dotnet build`

Run tests

`dotnet test`

Create a NuGet package

`dotnet pack --configuration Release`

# Contributing
When contributing to this repository, please first discuss the change you wish to make via issue, email, or any other method with the owners of this repository before making a change.

1. Fork the repository on GitHub
2. Clone the project to your own machine
3. Commit changes to your own branch
4. Push your work back up to your fork
5. Submit a Pull request so that we can review your changes

NOTE: Be sure to merge the latest from "upstream" before making a pull request!

# Change Log

| Version | Changes |
| ------- | ------- |
| 1.0.0   | The initial version. |
| 1.1.0   | DateTimes added to the result objects. |
| 1.2.0   | Added Keyboard-interactive auth |
| 1.3.0   | All possible auth combinations added (username, password, private key file, passphrase, keyboard interactive) |
| 2.0.0   | Version number update to enable easier update from older sftp package. |
| 2.1.0   | Added option to include subdirectories. |
