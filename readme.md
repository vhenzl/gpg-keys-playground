# GPG keys

Just trying to make sense of GPG and its keys…


gpg used:

```
gpg (GnuPG) 2.2.19
libgcrypt 1.8.5
Copyright (C) 2019 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Home: /home/vah/projects/gnupg
Supported algorithms:
Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2
```

pgpdump used:

```
pgpdump version 0.33, Copyright (C) 1998-2017 Kazu Yamamoto
```

GPG's homedir for this project: `export GNUPGHOME=~/projects/gnupg/`

Keys exported with:
```
gpg -armor --export 0CD3E41084CA1972 > gpg_public.asc && \
gpg -armor --export-secret-keys 0CD3E41084CA1972 > gpg_private.asc && \
gpg -armor --export-secret-subkeys 0CD3E41084CA1972 > gpg_private_sub.asc
```

Data files created with:

```
pgpdump gpg_public.asc -u > dump_public.txt && \
pgpdump gpg_private.asc -u > dump_private.txt && \
pgpdump gpg_private_sub.asc -u > dump_private_sub.txt && \
gpg --list-packets gpg_public.asc > packets_public.txt && \
gpg --list-packets gpg_private.asc > packets_private.txt && \
gpg --list-packets gpg_private_sub.asc > packets_private_sub.txt && \
gpg --list-secret-keys --keyid-format=long --with-fingerprint --with-fingerprint --with-keygrip > list.txt
```

Password used in `gpg --expert --full-gen-key`: `xyz123`. Each executed command is in corresponding commit message.
