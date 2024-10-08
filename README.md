## Hi there 👋

<!--
**trieuhung2005/trieuhung2005** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
        }
        for (Map.Entry<String, Double> entry : studentScores.entrySet()) {
            System.out.println("Mã sinh viên: " + entry.getKey() + ", Điểm: " + entry.getValue());
        }
    }

    public double calculateAverageScore() {
        if (studentScores.isEmpty()) {
            return 0;
        }
        double totalScore = 0;
        for (double score : studentScores.values()) {
            totalScore += score;
        }
        return totalScore / studentScores.size();
    }

    public void listStudentsAboveScore(double threshold) {
        System.out.println("Danh sách sinh viên có điểm lớn hơn " + threshold + ":");
        boolean found = false;
        for (Map.Entry<String, Double> entry : studentScores.entrySet()) {
            if (entry.getValue() > threshold) {
                System.out.println("Mã sinh viên: " + entry.getKey() + ", Điểm: " + entry.getValue());
                found = true;
            }
        }
        if (!found) {
            System.out.println("Không có sinh viên nào có điểm lớn hơn " + threshold + ".");
        }
    }

    public static void main(String[] args) {
        StudentScores scoresManager = new StudentScores();
        Scanner scanner = new Scanner(System.in);
        int choice;

        do {
            System.out.println("1. Thêm điểm sinh viên");
            System.out.println("2. Hiển thị danh sách sinh viên và điểm thi");
            System.out.println("3. Tính điểm trung bình");
            System.out.println("4. Liệt kê sinh viên có điểm lớn hơn giá trị cho trước");
            System.out.println("0. Thoát");
            System.out.print("Chọn thao tác: ");
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Nhập mã sinh viên: ");
                    String studentId = scanner.next();
                    System.out.print("Nhập điểm thi: ");
                    double score = scanner.nextDouble();
                    scoresManager.addScore(studentId, score);
                    break;
                case 2:
                    scoresManager.displayScores();
                    break;
                case 3:
                    double average = scoresManager.calculateAverageScore();
                    System.out.println("Điểm trung bình của tất cả sinh viên: " + average);
                    break;
                case 4:
                    System.out.print("Nhập điểm ngưỡng: ");
                    double threshold = scanner.nextDouble();
                    scoresManager.listStudentsAboveScore(threshold);
                    break;
                case 0:
                    System.out.println("Thoát chương trình.");
                    break;
                default:
                    System.out.println("Lựa chọn không hợp lệ, vui lòng thử lại.");
            }
        } while (choice != 0);

        scanner.close();
    }
}
