# About
- 他モジュール(スタブ、モック等)の切り替え方法例
- 想定ユースケース
	- 他チームが開発するモジュールが出来上がるまでは自作のスタブを使用する。完成したら本コードに切り替える
	- ユニットテスト用にはモックを使用する。プロダクトコード用には、本コードに切り替える

- 切り替え方法
	- `#ifdef`で切り替える
		- コードが汚れる
		- 本コードが、ユニットテスト中にコンパイルされない
	- Link時にファイル指定して切り替える
		- 本コードが、ユニットテスト中にコンパイルされない
		- あるテストではモックを使うが、別のテストでは本コードを使う、といったことが出来ない
	- 関数ポインタ
	- 関数テーブルを持った構造体
	- Interface
		- C++のみ

- 必要に応じて、Wrapperをかませる
	- モジュールが他チーム提供だったりOS機能の場合には、Wrapperをかませた方がいい
		- ↑の切り替え方法を使えるのは、インターフェイスがしっかり決まっているとき
		- Wrapper経由にすることで、インターフェイスを自分で決められる
		- インターフェイスの差異(エラーコードの数字など)は、Wrapperで吸収できる
	- Wrapper関数に対して、↑と同じ切り替え方法を使える

