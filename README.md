# learn-branch2

ブランチ運用の検証

## 概要

- 現在のブランチ運用そのままにマージ方式を `Squash and merge` に一本化できないか検証する。

## 検証シナリオ

### 通常パターン

- ブランチ1
  - [x] コミット 1.1
  - [x] コミット 1.2
  - [x] PR 作成 ( to `qa` )
  - [x] Squash & Merge
- ブランチ2
  - [ ] コミット 2.1
  - [ ] コミット 2.2
  - [ ] PR 作成 ( to `qa` )
  - [ ] Squash & Merge
- リリース
  - [ ] PR 作成 ( to `master` )
  - [ ] Merge commit
  - [ ] タグ作成

### PR Chainパターン

- ブランチ3
  - [ ] コミット 3.1
  - [ ] コミット 3.2
  - [ ] PR 作成 ( to `qa` )
- ブランチ4
  - [ ] コミット 4.1
  - [ ] コミット 4.2
  - [ ] PR 作成 ( to `ブランチ3` )
- ブランチ3 (2)
  - [ ] Squash & Merge
- ブランチ4 (2)
  - [ ] マージ先を `qa` に変更
  - [ ] Squash & Merge
- リリース
  - [ ] PR 作成 ( to `master` )
  - [ ] Merge commit
  - [ ] タグ作成

### Rebase 取り込みパターン

- ブランチ5
  - [ ] コミット 5.1
  - [ ] コミット 5.2
  - [ ] PR 作成 ( to `qa` )
- ブランチ6
  - [ ] コミット 6.1
  - [ ] コミット 6.2
  - [ ] PR 作成 ( to `qa` )
- ブランチ5 (2)
  - [ ] Squash & Merge
- ブランチ6 (2)
  - [ ] `git rebase` して最新の `qa` を取り込む
  - [ ] Squash & Merge
- リリース
  - [ ] PR 作成 ( to `master` )
  - [ ] Merge commit
  - [ ] タグ作成

### Merge 取り込みパターン

- ブランチ7
  - [ ] コミット 7.1
  - [ ] コミット 7.2
  - [ ] PR 作成 ( to `qa` )
- ブランチ8
  - [ ] コミット 8.1
  - [ ] コミット 8.2
  - [ ] PR 作成 ( to `qa` )
- ブランチ7 (2)
  - [ ] Squash & Merge
- ブランチ8 (2)
  - [ ] `git merge` して最新の `qa` を取り込む
  - [ ] Squash & Merge

### Hot Fix パターン

- ブランチ9
  - [ ] コミット 9.1
  - [ ] コミット 9.2
  - [ ] PR 作成 ( to `master` )
  - [ ] Merge commit
- リリース
  - [ ] タグ作成
- 取り込み
  - [ ] PR 作成 ( to `qa` from `master` )
  - [ ] Squash & Merge
