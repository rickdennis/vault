---
layout: "docs"
page_title: "Upgrading to Vault 1.3.0 - Guides"
sidebar_title: "Upgrade to 1.3.0"
sidebar_current: "docs-upgrading-to-1.3.0"
description: |-
  This page contains the list of deprecations and important or breaking changes
  for Vault 1.3.0. Please read it carefully.
---

# Overview

This page contains the list of deprecations and important or breaking changes
for Vault 1.3.0 compared to 1.2.4. Please read it carefully.

## Secondary cluster activation 

There has been a change to the way that activating performance and DR secondary
clusters works when using public keys for encryption of the parameters rather
than a wrapping token. This flow was experimental and never documented. It is
now officially supported and documented but is not backwards compatible with
older Vault releases.

## Cluster cipher suites 

On its cluster port, Vault will no longer advertise the full TLS 1.2 cipher
suite list by default. Although this port is only used for Vault-to-Vault
communication and would always pick a strong cipher, it could cause false flags
on port scanners and other security utilities that assumed insecure ciphers were
being used. The previous behavior can be achieved by setting the value of the
(undocumented) cluster_cipher_suites config flag to tls12.
