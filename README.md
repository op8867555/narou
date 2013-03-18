Narou.rb ― 小説家になろうダウンローダ＆縦書用整形スクリプト
============================================================

概要 - Summary
--------------
このアプリは[小説家になろう](http://syosetu.com/)で公開されている小説の管理、及び電子書籍データへの
変換を支援します。縦書用に特化されており、横書き用に特化されたWEB小説を違和感なく縦書で読むことが出来るようになります。

全てコンソールで操作するCUIアプリケーションです。

主な機能は小説家になろうの小説のダウンロード、更新管理、テキスト整形、AozoraEpub3・kindlegen連携によるEPUB/MOBI出力です。

縦書に特化しており、どんな文章だろうとほぼ違和感なく縦書で読むことができるように変換します。また、若干の校正機能もありますので、
小説としては許されない記述法などは矯正します。（例：感嘆符のあとにはスペースが必ずくる）

詳細な説明やインストール方法は **[Narou.rb 説明書](https://github.com/whiteleaf7/narou/wiki)** を御覧ください。

更新履歴 - ChangeLog
--------------------
2013/03/19 : **1.2.0**
* Bug Fix 及び機能改善
	- Windows以外のOSでの動作状況を改善しました(Ubuntu Linuxで確認。Mac OS Xは未確認だが恐らく動くはず)
		+ Nコードを指定した場合にエラーが出ていたのを修正
		+ AozoraEpub3の出力をうまく扱えていなくエラーが出ていたのを修正
		+ Linuxでも `folder` 及び `browser` コマンドを使えるように改善
		+ `send` コマンドでデバイスへ送信出来るように(Linuxのみ確認、Mac OS Xは未確認)
			- /media もしくは /mnt を探します。送信出来ない場合はこのフォルダにマウントされているか確認して下さい
	- shebangの記述をちゃんと動くように修正(gem でインストールした場合は影響なし)
	- --no-color 時の処理の最適化
* 追加機能もしくは仕様変更
	- 漢数字の単位化下限のデフォルトを3桁から4桁へ変更(kanji_num_with_units_lower_digit_zero=3)
		+ `100 → 一〇〇、1000 → 千` と変換される
	- 章タイトルページの柱の位置調整
	- 行頭二分アキをいれる対象にノノカギ（〝）を追加
	- ！？の直後に全角アキを自動挿入しないパターンに閉じノノカギ（〟）を追加
	- 小説のDL時に最初から用意された変換設定を適用する機能追加
		+ 以下の小説の設定を同梱しました（気まぐれで増えていきます）
			- [オーバーロード：後編](http://ncode.syosetu.com/n1839bd/)
			- [異世界迷宮で奴隷ハーレムを](http://ncode.syosetu.com/n4259s/)
			- [ログ・ホライズン](http://ncode.syosetu.com/n8725k/)
			- [無職転生　- 異世界行ったら本気だす -](http://ncode.syosetu.com/n9669bk/)

2013/03/18 : **1.1.2.1**
* Bug Fix
	- Linuxで実行不可能になるエラー修正

2013/03/17 : **1.1.2**
* Bug Fix
	- Fiddleがない環境でエラーになってたので修正
	- 同一行に（）と《》のルビが混在していた時に正しく処理出来ていなかったのを修正
	- 短編小説をDLしようとした時にDL出来ない旨メッセージを表示するように
	- ！？の縦中横化で自然ではない変換パターンに対応
* 追加機能もしくは仕様変更
	- なろうのルビ仕様に追随
		+ 全角空白もルビ対象として許容する
		+ サブタイトルのカッコはルビをふらない
	- 中黒(・)を３個以上連続して使っているのを三点リーダーに変換する機能実装
		+ `setting.ini` に `enable_convert_horizontal_ellipsis` を追加
	- 表示を若干色つけするように
		+ 色つけを抑制にするには `--no-color` オプションか `narou s no-color=true` で
	- 節のタイトル（中見出し）の位置を若干調整 (template/novel.txt.erb)

2013/03/09 : **1.1.1**
* Bug Fix
	- URL文字列のリンクを a タグに変更し忘れ修正
	- update コマンドにIDを直指定した時の変換時に不正な引数を渡していたのを修正
* 追加機能もしくは仕様変更
	- 三点リーダーの偶数化を１つからするように変更
