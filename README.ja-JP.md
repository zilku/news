# NewsNow

![](screenshots/preview-1.png)
![](screenshots/preview-2.png)

[English](./README.md) | [简体中文](README.zh-CN.md) | 日本語

> [!NOTE]
> 本バージョンはデモ版であり、現在中国語のみ対応しています。カスタマイズ機能や英語コンテンツをサポートした正式版は後日リリース予定です。

***リアルタイムで最新のニュースをエレガントに読む***

## 機能
- 最適な読書体験のためのクリーンでエレガントなUIデザイン
- トレンドニュースのリアルタイム更新
- GitHub OAuthログインとデータ同期
- デフォルトのキャッシュ期間は30分（ログインユーザーは強制更新可能）
- リソース使用を最適化し、IPブロックを防ぐためのソース更新頻度に基づく適応型スクレイピング間隔（最短2分）

## デプロイ

### 基本デプロイ
ログインとキャッシュ機能なしでデプロイする場合：
1. このリポジトリをフォーク
2. Cloudflare PagesやVercelなどのプラットフォームにインポート

### Cloudflare Pages設定
- ビルドコマンド：`pnpm run build`
- 出力ディレクトリ：`dist/output/public`

### GitHub OAuth設定
1. [GitHub Appを作成](https://github.com/settings/applications/new)
2. 特別な権限は不要
3. コールバックURLを設定：`https://your-domain.com/api/oauth/github`（your-domainを実際のドメインに置き換え）
4. Client IDとClient Secretを取得

### 環境変数
`example.env.server`を参照。ローカル開発では、`.env.server`にリネームして以下を設定：

```env
# GitHub Client ID
G_CLIENT_ID=
# GitHub Client Secret
G_CLIENT_SECRET=
# JWT Secret（通常はClient Secretと同じ）
JWT_SECRET=
# データベース初期化（初回実行時はtrueに設定）
INIT_TABLE=true
# キャッシュを有効にするかどうか
ENABLE_CACHE=true
```

### データベースサポート
対応データベースコネクタ： https://db0.unjs.io/connectors Cloudflare D1 Database を推奨。

1. Cloudflare WorkerダッシュボードでD1データベースを作成
2. `wrangler.toml` に `database_id` と `database_name` を設定
3. `wrangler.toml` が存在しない場合、 `example.wrangler.toml` をリネームして設定を変更
4. 次回デプロイ時に変更が反映

### Dockerデプロイ
プロジェクトルートディレクトリで：

```sh
docker compose up
 ```

環境変数は `docker-compose.yml` でも設定可能。

## 開発
> [!TIP]
> Node.js >= 20が必要

```sh
corepack enable
pnpm i
pnpm dev
 ```

### データソースの追加
`shared/sources` と `server/sources` ディレクトリを参照。プロジェクトは完全な型定義とクリーンなアーキテクチャを提供します。

## ロードマップ
- **多言語サポート**の追加（英語、中国語、その他言語を順次対応）
- **パーソナライズオプション**の改善（カテゴリ別ニュース、保存された設定）
- **データソース**の拡充による多言語対応のグローバルニュースカバレッジ

## コントリビューション
コントリビューションを歓迎します！機能リクエストやバグレポートのために、プルリクエストやイシューの作成をお気軽にどうぞ。

## ライセンス
MIT 

# 🙏 感谢
[ourongxing](https://github.com/ourongxing/newsnow/)

 # 
<center>
<details><summary><strong> [点击展开] 赞赏支持 ~🧧</strong></summary>
*我非常感谢您的赞赏和支持，它们将极大地激励我继续创新，持续产生有价值的工作。*

- **USDT-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`
- **TRX-TRC20:** `TWTxUyay6QJN3K4fs4kvJTT8Zfa2mWTwDD`

<div align="center"> 
  <img src="https://github.com/user-attachments/assets/e6cdc42a-6374-4722-b833-601738f72196" width="200"></br> 
  TRC10/TRC20扫码支付 
</div> 
</details>
</center>

 #
 免责声明:
 - 1、该项目设计和开发仅供学习、研究和安全测试目的。请于下载后 24 小时内删除, 不得用作任何商业用途, 文字、数据及图片均有所属版权, 如转载须注明来源。
 - 2、使用本程序必循遵守部署服务器所在地区的法律、所在国家和用户所在国家的法律法规。对任何人或团体使用该项目时产生的任何后果由使用者承担。
 - 3、作者不对使用该项目可能引起的任何直接或间接损害负责。作者保留随时更新免责声明的权利，且不另行通知。
